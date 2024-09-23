<template>
  <div class="rounded-md shadow-md bg-white">
    <!-- Your page content here -->
    <div class="flex justify-between items-center px-3 py-0.5">
      <h2 class="text-xl text-blue-900 font-bold">{{ displayCusId }}</h2>
    </div>
    <div class="border-b">
      <h3 class="font-medium mb-1 px-3">{{ displayCompanyName }}</h3>
      <p class="text-gray-600 font-medium px-3">{{ displayState }}</p>
      <p
        class="px-3"
        :class="coordinates ? 'text-gray-500' : 'text-error'"
      >
        <span class="text-blue-900">GPS</span>
        <span
          class="px-3 text-error text-sm"
          v-if="!coordinates"
          ><VIcon
            icon="ri-information-line"
            size="18"
            color="error"
            class="mb-1"
          />
          Please Enable Location & reload</span
        >
        {{ coordinates ? `${coordinates.latitude}, ${coordinates.longitude}` : ' ' }}
      </p>
    </div>

    <div v-if="questions[currentIndex]">
      <div class="mb-2 px-3">
        <div class="question-container">
          <h4 class="text-lg text-blue-900 font-medium mb-2 h-200">{{ questions[currentIndex].question }}</h4>
          <div v-if="questions[currentIndex].parts">
            <div
              v-for="(part, index) in questions[currentIndex].parts"
              :key="index"
            >
              <h5 class="text-md text-blue-900 font-medium mb-1">{{ part.part }}</h5>
            </div>
          </div>
          <div class="flex justify-between mb-2">
            <label class="inline-flex items-center mb-5 cursor-pointer">
              <span class="mr-3 text-sm font-medium text-gray-700 dark:text-gray-300">yes</span>
              <input
                type="checkbox"
                :value="this.questions[currentIndex].isMessageMandatory"
                :checked="this.questions[currentIndex].isMessageMandatory"
                @input="
                  updateYesNoAnswer(
                    questions[currentIndex].questionId,
                    $event.target.checked,
                    questions[currentIndex].isMessageMandatory,
                  )
                "
                class="sr-only peer"
              />
              <div
                class="relative w-9 h-5 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-300 dark:peer-focus:ring-blue-800 rounded-full peer dark:bg-gray-700 peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-4 after:w-4 after:transition-all dark:border-gray-600 peer-checked:bg-blue-600"
              ></div>
              <span class="ms-3 text-sm font-medium text-gray-700 dark:text-gray-300">no</span>
            </label>
          </div>
          <!-- rest of the question content -->
        </div>
        <div v-if="questions[currentIndex].isLiveCameraMandatory == true">
          <div class="w-full border-dotted border-2 rounded h-40 relative my-4">
            <!-- Show picture image initially -->
            <div
              class="absolute inset-0 flex flex-col justify-center items-center py-20"
              v-if="!showCamera && !capturedImages[currentIndex]"
              @click="toggleCamera"
            >
              <img
                src="@/public/picture.png"
                alt="Placeholder"
                class="w-10 h-10 object-cover"
              />
              <div>
                <div class="mt-2 font-bold">Live Capture <span class="text-error"> *</span></div>
              </div>
            </div>

            <!-- Live Camera Feed -->

            <video
              ref="video"
              v-if="showCamera && !capturedImage"
              class="absolute inset-0 w-full h-full object-cover"
              autoplay
            ></video>

            <!-- Captured Image -->
            <!-- <img
            v-if="capturedImage"
            :src="capturedImage"
            class="absolute inset-0 w-full h-full object-cover"
          /> -->
            <img
              v-if="capturedImages[currentIndex]"
              :src="capturedImages[currentIndex]"
              class="absolute inset-0 w-full h-full object-cover"
            />
          </div>
          <!-- Capture button only shown when live camera feed is displayed -->
          <div
            v-if="showCamera && !capturedImage"
            class="py-3"
          >
            <button
              @click="capture"
              class="bg-blue-900 hover:bg-blue-700 text-white font-bold py-2 rounded w-full"
            >
              Capture
            </button>
            <!-- <button
            @click="switchCamera"
            class="bg-blue-900 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded w-100"
          >
            Switch Camera
          </button> -->
          </div>
          <div
            v-if="capturedImages[currentIndex]"
            class="py-3"
          >
            <button
              @click="retake"
              class="bg-gray-200 hover:bg-gray-300 text-gray-600 font-bold py-2 px-4 rounded w-100"
            >
              Retake
            </button>
          </div>
        </div>
        <div>
          <div v-if="questions[currentIndex].isMessageMandatory">
            <textarea
              id="message"
              rows="3"
              v-model="notes[currentIndex]"
              placeholder="  Optional Message / Notes  "
              class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            ></textarea>
          </div>
          <div v-else>
            <textarea
              id="message"
              rows="3"
              v-model="notes[currentIndex]"
              placeholder="  Optional Message / Notes * "
              class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            ></textarea>
          </div>
        </div>
        <div class="text-gray-600">Question {{ currentIndex + 1 }} of {{ questions.length }}</div>
      </div>
      <div class="flex justify-between p-3">
        <button
          @click="previousStep"
          :disabled="currentIndex <= 0"
          class="border border-gray-500 text-gray-500 font-bold py-2 px-4 w-100 mr-2 rounded"
          :class="{ 'bg-gray-200': currentIndex <= 0 }"
        >
          ← Previous
        </button>
        <button
          @click="nextStep"
          class="bg-blue-900 hover:bg-blue-700 text-white font-bold py-2 px-4 ml-2 w-100 rounded"
          :disabled="this.currentIndex >= this.questions.length - 1"
          :class="{ 'bg-gray-200 hover:bg-gray-200': this.currentIndex >= this.questions.length - 1 }"
        >
          Next →
        </button>
        <Pagination
          :pages="pages"
          :prev="prev"
          :next="next"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import axios from 'axios'
// import { userDataStore } from '~/stores/tableData'
// const userStore = userDataStore()
export default {
  data() {
    return {
      yesNoAnswers: {},
      image: null,
      currentStream: null,
      facingMode: 'environment',
      showCamera: false,
      coordinates: null,
      questions: [],
      notes: [],
      currentIndex: 0,
      pages: [],
      prev: null,
      next: null,
      capturedImages: [],
      isLastQuestion: false,
      cusId: null,
      empId: null,
      empName: null,
      companyName: null,
      state: null,
    }
  },
  mounted() {
    this.startCamera(),
      this.getLocation(),
      this.fetchData(),
      (this.yesNoAnswers = new Array(this.questions.length).fill(false))
    this.cusId = this.$route.query.customerId ? this.$route.query.customerId : 'GZ10219'
    console.log(this.cusId, ' this.cusId')
    this.empName = this.$route.query.employeeName ? this.$route.query.employeeName : 'GZ10219'
    console.log(this.empName, ' this.empName')
    this.empId = this.$route.query.employeeId ? this.$route.query.employeeId : 'GZ10219'
    console.log(this.empId, ' this.empId')
    this.companyName = this.$route.query.clientCompanyName ? this.$route.query.clientCompanyName : 'GZ10219'
    console.log(this.companyName, ' this.companyName')
    this.state = this.$route.query.state ? this.$route.query.state : 'GZ10219'
    console.log(this.state, ' this.state')
    //userStore.setUser(this.empName, this.empId)
  },
  computed: {
    displayCusId() {
      return this.cusId ? this.cusId : ''
    },
    displayCompanyName() {
      return this.companyName ? this.companyName : ''
    },
    displayState() {
      return this.state ? this.state : ''
    },
  },
  methods: {
    updateYesNoAnswer(questionId, value, index) {
      console.log(index, 'index')
      const currentQuestionIndex = this.questions.findIndex(question => question.questionId === questionId)
      console.log(currentQuestionIndex, 'currentQuestionIndex')
      if (currentQuestionIndex !== -1) {
        this.questions[currentQuestionIndex].isMessageMandatory = value
      }
      console.log(index, 'indexfinal', this.questions[currentQuestionIndex].isMessageMandatory)
    },
    toggleCamera() {
      this.showCamera = !this.showCamera
      if (this.showCamera) {
        this.startCamera()
      }
    },
    async startCamera() {
      this.currentStream = await navigator.mediaDevices.getUserMedia({ video: { facingMode: this.facingMode } })
      this.$refs.video.srcObject = this.currentStream
    },
    // async switchCamera() {
    //   this.facingMode = this.facingMode === 'user' ? 'environment' : 'user'
    //   await this.startCamera()
    // },
    // capture() {
    //   const canvas = document.createElement('canvas')
    //   const video = this.$refs.video
    //   const context = canvas.getContext('2d')
    //   canvas.width = video.videoWidth
    //   canvas.height = video.videoHeight
    //   context.drawImage(video, 0, 0, canvas.width, canvas.height)
    //   this.capturedImage = canvas.toDataURL('image/png')
    //   this.showCamera = false
    //   console.log(this.capturedImage, '  this.capturedImage ')
    // },
    capture() {
      const canvas = document.createElement('canvas')
      const video = this.$refs.video
      const context = canvas.getContext('2d')
      canvas.width = video.videoWidth
      canvas.height = video.videoHeight
      context.drawImage(video, 0, 0, canvas.width, canvas.height)
      const capturedImage = canvas.toDataURL('image/png')
      this.capturedImages[this.currentIndex] = capturedImage // store the captured image for the current question
      this.showCamera = false
      console.log(this.capturedImages, 'this.capturedImages')
    },

    async getLocation() {
      try {
        navigator.geolocation.getCurrentPosition(
          position => {
            this.coordinates = {
              latitude: position.coords.latitude,
              longitude: position.coords.longitude,
            }
            this.locationLoading = false
          },
          error => {
            if (error.code === 1) {
              // PERMISSION_DENIED
              console.error('Location permission denied')
              // You can display a prompt to the user to grant permission
              alert('Please grant location permission to continue')
            } else {
              console.error('Error getting location:', error)
            }
            this.locationLoading = false
          },
          { enableHighAccuracy: true },
        )
      } catch (error) {
        console.error('Error getting location:', error)
      }
    },
    retake() {
      this.showCamera = true
      this.capturedImage = null
      this.capturedImages[this.currentIndex] = null
      this.startCamera()
    },
    async fetchData() {
      try {
        // const response = await axios.get('https://g1.gwcindia.in/ap_inspection/get-questions.php')
        const response = [
          {
            questionId: '1',
            question: '1 Whether all clients are registered directly with the Trading Member only.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Dealing with clients',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '2',
            question: '2 There is no movement of Funds and securities between the clients and AP.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Dealing with clients',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '3',
            question: '3 There are no fixed payments at regular intervals to the clients mapped to AP.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Dealing with clients',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '4',
            question: '4 There are no cash dealings done with clients by AP.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Dealing with clients',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '5',
            question:
              '5 The AP is not involved in any fund-based activities / collecting deposits from investors / unauthorised trading or any other such schemes.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Dealing with clients',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '6',
            question: '6 The AP is not involved in any illegal/dabba/paper trading.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Dealing with clients',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '7',
            question: '7 The AP has not dealt with any unregistered intermediary on behalf of its clients/self.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Dealing with clients',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '8',
            question:
              '8 The AP is not involved in accepting deposits from the public and giving assured returns to their clients.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Dealing with clients',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '9',
            question:
              '9 Complaints received against AP pertaining to Assured Returns / Unauthorised Trading / Dabba Trading / associated with unregistered intermediary.',
            isMessageMandatory: false,
            isLiveCameraMandatory: true,
            type_name: 'Dealing with clients',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '10',
            question: '10 The AP does not offer any incentives to clients for opening trading accounts.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Dealing with clients',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '11',
            question: '11 AP has sought any authorisation to trade on behalf of its clients.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Dealing with clients',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '12',
            question:
              '12 Advertisements for soliciting business are not issued by the APs in newspapers / pamphlets / journals / magazines / emails including social media like Facebook, Instagram, telegram channels etc., without seeking appropriate approvals from the Exchange, through the Trading Member. This includes not publishing performance returns etc.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '13',
            question: '13 All AP terminals are as per the information reported to the Exchange.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Terminal operations and related systems',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '14',
            question: '14 Trading terminals are operated by approved and certified users.',
            isMessageMandatory: false,
            isLiveCameraMandatory: true,
            type_name: 'Terminal operations and related systems',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '15',
            question:
              '15 Adequate systems, including voice recording, have been put in place, with a view to ensure recording of order placement from clients. Trading Members must ensure that APs who do not have trading terminals assigned to them, cannot place trades on behalf of the Trading Member’s clients.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Terminal operations and related systems',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '16',
            question:
              '16 Documents like contract notes, statement of funds, daily margin statement are not generated and issued by the AP. However, AP may provide	administrative assistance in procurement of documents from the Trading Member, after maintaining proper records of the same . ',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '17',
            question:
              '17 The AP has not dealt with / or associated with any other Trading Member/AP on behalf of its clients/self on the same Stock Exchange.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '18',
            question:
              '18 Trading activities/Turnover of AP/Clients mapped with the AP	are	monitored,	and necessary actions/investigations are undertaken on a timely basis.',
            isMessageMandatory: false,
            isLiveCameraMandatory: true,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '19',
            question:
              '19 The AP has the necessary infrastructure like adequate office space, equipment, and manpower to effectively discharge the activities on behalf of the Trading Member.',
            isMessageMandatory: false,
            isLiveCameraMandatory: true,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '20',
            question:
              '20 Complaints received by and against the APs are handled appropriately and proper records are maintained',
            isMessageMandatory: false,
            isLiveCameraMandatory: true,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '21',
            question: '21 Proper segregation and demarcation are maintained at AP office.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '22',
            question:
              '22 Notice board of the Trading Member	containing	all details/information prescribed from time to time, are displayed at the AP/s location.',
            isMessageMandatory: false,
            isLiveCameraMandatory: true,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '23',
            question:
              '23 SEBI registration certificate of the Trading Member and registration letter issued by the Exchange is displayed at the location.',
            isMessageMandatory: false,
            isLiveCameraMandatory: true,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '24',
            question:
              '24 As required by SEBI circular CIR/MIRSD/3/2014 dated August 28, 2014, information about the grievance redressal mechanism available to investors is prominently displayed at the location.',
            isMessageMandatory: false,
            isLiveCameraMandatory: true,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '25',
            question:
              '25 Branch/AP records/data are properly maintained with confidentiality in a secure manner including sufficient backup.',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '26',
            question:
              '26.1 Branch/AP records/data are properly maintained with confidentiality in a secure manner including sufficient backup. a) All clients mapped to the AP/Branch are notified at least thirty days before the change.',
            type_name: 'Management of branches / AP and internal control',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            time: 'time',
            date: 'date',
          },

          {
            questionId: '27',
            question:
              '26.2 Branch/AP records/data are properly maintained with confidentiality in a secure manner including sufficient backup.b) Notice Board and applicable SEBI registration certificates are immediately put up at the new location.',
            type_name: 'Management of branches / AP and internal control',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            time: 'time',
            date: 'date',
          },
          {
            questionId: '28',
            question:
              '26.3 Branch/AP records/data are properly maintained with confidentiality in a secure manner including sufficient backup.c) The new location, including details of terminals if any, have been duly reported to the Exchange, and the old location, including terminals at the old location if any have been deactivated.',
            type_name: 'Management of branches / AP and internal control',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            time: 'time',
            date: 'date',
          },
          {
            questionId: '29',
            question:
              '26.4 Branch/AP records/data are properly maintained with confidentiality in a secure manner including sufficient backup.d) At the new location, adequate systems including voice recording, display of Notice Board and SEBI Registration certificates, and terminals etc. have been promptly installed to ensure the smooth functioning of business operations and the recording of order placements  from clients.',
            type_name: 'Management of branches / AP and internal control',
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            time: 'time',
            date: 'date',
          },
          {
            questionId: '30',
            question:
              "27 Any changes in the AP's contact details, such as registered / communication address, email address, mobile number or any changes in the Directors/ Partners of AP, are not reported/ incorrectly reported to the Members.",
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
          {
            questionId: '31',
            question:
              "28 The AP's mobile number, and email address are not mapped to any of its client in UCC uploaded to Exchange.",
            isMessageMandatory: false,
            isLiveCameraMandatory: false,
            type_name: 'Management of branches / AP and internal control',
            time: 'time',
            date: 'date',
          },
        ]

        this.questions = response.map(question => ({ ...question, isMessageMandatory: false }))
        this.notes = new Array(this.questions.length).fill('')

        console.log(response.data, 'response.data')

        // Create pagination
        this.pages = this.questions.map((question, index) => ({
          href: `/question/${index + 1}`,
          text: `Question ${index + 1}`,
        }))
        this.prev = this.currentIndex > 0 ? { href: `/question/${this.currentIndex}`, text: 'Previous' } : null
        this.next =
          this.currentIndex < this.questions.length - 1
            ? { href: `/question/${this.currentIndex + 2}`, text: 'Next' }
            : null
      } catch (err) {
        console.error('Error:', err)
      } finally {
      }
    },
    nextStep() {
      if (this.currentIndex < this.questions.length - 1) {
        this.currentIndex++
        this.showCamera = false
        this.capturedImage = null
        console.log(
          this.questions[this.currentIndex].isMessageMandatory,
          'this.questions[currentIndex].isMessageMandatory',
        )
      } else {
        this.next = null
      }
    },

    previousStep() {
      if (this.currentIndex > 0) {
        this.currentIndex--
        this.showCamera = false
        this.capturedImage = null
      } else {
        this.prev = null
      }
    },
    async postData() {
      try {
        // Prepare the data
        const questions = this.questions.map((question, index) => {
          return {
            questionId: question.id,
            question: question.question,
            message: this.notes[index],
            Image: this.capturedImages[index],
            type: question.type,
            EmpId: 'GUD001',
            customerId: 'A101',
            companyName: 'Finy Wealth',
            state: 'Andhra Pradesh',
            lat: this.coordinates.latitude,
            lan: this.coordinates.longitude,
            data: new Date().toISOString(),
            time: new Date().toLocaleTimeString(),
          }
        })

        // Make a POST request to the API
        const response = await axios.post('https://your-api-url.com/submit-questions', {
          questions,
        })

        console.log(response.data)
      } catch (err) {
        console.error('Error:', err)
      }
    },
  },
}
</script>


<style scoped>
.question-container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  /* height: 200px; adjust the height value as needed */
}
.relative {
  position: relative;
}
.absolute {
  position: absolute;
}
.inset-0 {
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
.object-cover {
  object-fit: cover;
}
</style>
