<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import RecentItem from './RecentItem.vue';
import avatar1 from "../assets/images/avatar-searches-1.svg"


const isAllModalOpen = ref(false);
const isAiModalOpen = ref(false);
const isChatOpen = ref(false);
const activeModal = ref(null);

const toggleAllModal = () => {
  isAllModalOpen.value = !isAllModalOpen.value;

  if (isAllModalOpen.value) {
    isAiModalOpen.value = false;
    isChatOpen.value = false;
    document.body.style.overflow = "hidden";
  } else {
    document.body.style.overflow = "";
  }
};

const toggleAiModal = () => {
  isAiModalOpen.value = !isAiModalOpen.value;

  if (isAiModalOpen.value) {
    isAllModalOpen.value = false;
    isChatOpen.value = false;
    document.body.style.overflow = "hidden";
  } else {
    document.body.style.overflow = "";
  }
};

const toggleCalendar = () => {
  activeModal.value = activeModal.value === "calendar" ? null : "calendar";
  document.body.style.overflow = activeModal.value ? "hidden" : "";
};

const closeModals = () => {
  activeModal.value = null;
  document.body.style.overflow = "";
};

const openChat = () => {
  isChatOpen.value = true;

  isAiModalOpen.value = false;
  isAllModalOpen.value = false;
  document.body.style.overflow = "hidden";
  document.querySelector('header')?.classList.add('active');
};

const closeChat = () => {
  isChatOpen.value = false;
  isAiModalOpen.value = false;
  isAllModalOpen.value = false;
  document.body.style.overflow = "";
  document.querySelector('header')?.classList.remove('active');
};

if (isAiModalOpen.value || isAllModalOpen.value || isChatOpen.value) {
  document.body.style.overflow = "hidden";
} else {
  document.body.style.overflow = "";
}

const onOverlayClick = () => {
  isChatOpen.value = false;
  document.querySelector('header')?.classList.remove('active');
};

function handleClickOutside(e) {
  const aiModal = document.querySelector(".modal-ai-assist");
  const aiBtn = document.querySelector(".ai-assist-btn");

  const allModal = document.querySelector(".all-modal-selector");
  const allBtn = document.querySelector(".all-btn");

  const chatModal = document.querySelector(".chat");
  
  if (isAiModalOpen.value) {
    if (
      aiModal &&
      !aiModal.contains(e.target) &&
      !aiBtn.contains(e.target)
    ) {
      isAiModalOpen.value = false;
    }
  }

  if (isAllModalOpen.value) {
    if (
      allModal &&
      !allModal.contains(e.target) &&
      !allBtn.contains(e.target)
    ) {
      isAllModalOpen.value = false;
    }
  }

  if (isChatOpen.value) {
    if (
      chatModal &&
      !chatModal.contains(e.target)
    ) {
      isChatOpen.value = false;
    }
  }
}

onMounted(() => document.addEventListener("click", handleClickOutside));
onBeforeUnmount(() => document.removeEventListener("click", handleClickOutside));


const items = [
  {
    title: "Where can I find the new GDPR compliance rules?",
    user: "Ashlynn Herwitz",
    date: "2025-11-09, 08:24",
    status: "success",
    avatar: avatar1,

    aiAnswer: "To request remote work approval, start by reviewing your company’s remote work policy to ensure you meet all eligibility criteria. Then, prepare a short written request to your manager or HR, explaining the reason for your request, the duration, and how you plan to maintain productivity while working remotely. Include any tools or communication methods you’ll use to stay connected. Once submitted, wait for feedback or further instructions from your supervisor.",
    aiAnswerDate: "2025-11-09, 08:25",

    comment: "This answer was really helpful! It clearly explained each step I need to take and reminded me to check the company policy first, which I hadn’t considered.",
    commentDate: "2025-11-09, 11:24",
    showComment: true,
  },
    {
    title: "Where can I find the new GDPR compliance rules?",
    user: "Ashlynn Herwitz",
    date: "2025-11-09, 08:24",
    status: "success",
    avatar: avatar1,

    aiAnswer: "To request remote work approval, start by reviewing your company’s remote work policy to ensure you meet all eligibility criteria. Then, prepare a short written request to your manager or HR, explaining the reason for your request, the duration, and how you plan to maintain productivity while working remotely. Include any tools or communication methods you’ll use to stay connected. Once submitted, wait for feedback or further instructions from your supervisor.",
    aiAnswerDate: "2025-11-09, 08:25",

    comment: "This answer was really helpful! It clearly explained each step I need to take and reminded me to check the company policy first, which I hadn’t considered.",
    commentDate: "2025-11-09, 11:24",
    showComment: true,
  },
    {
    title: "Where can I find the new GDPR compliance rules?",
    user: "Ashlynn Herwitz",
    date: "2025-11-09, 08:24",
    status: "error",
    avatar: avatar1,

    aiAnswer: "To request remote work approval, start by reviewing your company’s remote work policy to ensure you meet all eligibility criteria. Then, prepare a short written request to your manager or HR, explaining the reason for your request, the duration, and how you plan to maintain productivity while working remotely. Include any tools or communication methods you’ll use to stay connected. Once submitted, wait for feedback or further instructions from your supervisor.",
    aiAnswerDate: "2025-11-09, 08:25",

    comment: "This answer was really helpful! It clearly explained each step I need to take and reminded me to check the company policy first, which I hadn’t considered.",
    commentDate: "2025-11-09, 11:24",
    showComment: true,
  },
    {
    title: "Where can I find the new GDPR compliance rules?",
    user: "Ashlynn Herwitz",
    date: "2025-11-09, 08:24",
    status: "neutral",
    avatar: avatar1,

    aiAnswer: "To request remote work approval, start by reviewing your company’s remote work policy to ensure you meet all eligibility criteria. Then, prepare a short written request to your manager or HR, explaining the reason for your request, the duration, and how you plan to maintain productivity while working remotely. Include any tools or communication methods you’ll use to stay connected. Once submitted, wait for feedback or further instructions from your supervisor.",
    aiAnswerDate: "2025-11-09, 08:25",

    comment: "This answer was really helpful! It clearly explained each step I need to take and reminded me to check the company policy first, which I hadn’t considered.",
    commentDate: "2025-11-09, 11:24",
    showComment: true,
  },
    {
    title: "Where can I find the new GDPR compliance rules?",
    user: "Ashlynn Herwitz",
    date: "2025-11-09, 08:24",
    status: "success",
    avatar: avatar1,

    aiAnswer: "To request remote work approval, start by reviewing your company’s remote work policy to ensure you meet all eligibility criteria. Then, prepare a short written request to your manager or HR, explaining the reason for your request, the duration, and how you plan to maintain productivity while working remotely. Include any tools or communication methods you’ll use to stay connected. Once submitted, wait for feedback or further instructions from your supervisor.",
    aiAnswerDate: "2025-11-09, 08:25",

    comment: "This answer was really helpful! It clearly explained each step I need to take and reminded me to check the company policy first, which I hadn’t considered.",
    commentDate: "2025-11-09, 11:24",
    showComment: true,
  },
    {
    title: "Where can I find the new GDPR compliance rules?",
    user: "Ashlynn Herwitz",
    date: "2025-11-09, 08:24",
    status: "success",
    avatar: avatar1,

    aiAnswer: "To request remote work approval, start by reviewing your company’s remote work policy to ensure you meet all eligibility criteria. Then, prepare a short written request to your manager or HR, explaining the reason for your request, the duration, and how you plan to maintain productivity while working remotely. Include any tools or communication methods you’ll use to stay connected. Once submitted, wait for feedback or further instructions from your supervisor.",
    aiAnswerDate: "2025-11-09, 08:25",

    comment: "This answer was really helpful! It clearly explained each step I need to take and reminded me to check the company policy first, which I hadn’t considered.",
    commentDate: "2025-11-09, 11:24",
    showComment: false,
  },
];
</script>

<template>
  <section class="recent">
    <div class="block__header">
      <h3>Recent Searches</h3>
    </div>
    <div class="recent__inner">
  
      <div class="filters-row">
        <div class="filters-group">
          <div class="all-searches">
            <button ref="allBtn" @click="toggleAllModal">
              <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M2.08325 7.5H5.41659" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/>
              <path d="M2.08325 11.6666H5.41659" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/>
              <path d="M2.08325 3.33336H15.4166" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/>
              <path d="M15.4462 14.1963L17.9166 16.6667M16.6666 11.25C16.6666 8.94886 14.8011 7.08336 12.4999 7.08336C10.1988 7.08336 8.33325 8.94886 8.33325 11.25C8.33325 13.5512 10.1988 15.4167 12.4999 15.4167C14.8011 15.4167 16.6666 13.5512 16.6666 11.25Z" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              All searches
            </button>
            <div class="modal-all" v-if="isAllModalOpen" ref="allModal">
              <div class="modal-all__inner">
                <button>All searches</button>
                <button>Favorite</button>
                <button>Not useful</button>
                <button>Commented</button>
              </div>
            </div>
          </div>
          
          <div class="calendar">
                      <button @click="toggleCalendar">
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M9.16675 10.8334H13.3334H9.16675ZM6.66675 10.8334H6.67423H6.66675ZM10.8334 14.1667H6.66675H10.8334ZM13.3334 14.1667H13.3259H13.3334Z" fill="#110E12"/>
            <path d="M9.16675 10.8334H13.3334M6.66675 10.8334H6.67423M10.8334 14.1667H6.66675M13.3334 14.1667H13.3259" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M15 1.66664V3.33331V1.66664ZM5 1.66664V3.33331V1.66664Z" fill="#110E12"/>
            <path d="M15 1.66664V3.33331M5 1.66664V3.33331" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M2.08325 10.2027C2.08325 6.57162 2.08325 4.75607 3.12669 3.62803C4.17012 2.5 5.84949 2.5 9.20825 2.5H10.7916C14.1503 2.5 15.8298 2.5 16.8732 3.62803C17.9166 4.75607 17.9166 6.57162 17.9166 10.2027V10.6307C17.9166 14.2618 17.9166 16.0773 16.8732 17.2053C15.8298 18.3333 14.1503 18.3333 10.7916 18.3333H9.20825C5.84949 18.3333 4.17012 18.3333 3.12669 17.2053C2.08325 16.0773 2.08325 14.2618 2.08325 10.6307V10.2027Z" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M2.5 6.66664H17.5H2.5Z" fill="#110E12"/>
            <path d="M2.5 6.66664H17.5" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
              15-24 June 2025
            </button>
            <div v-if="activeModal === 'calendar'" class="calendar-widget">
            <div class="calendar-widget__header">
              <div class="calendar-header-group">
                <button class="calendar-nav prev"><svg width="6" height="8" viewBox="0 0 6 8" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M0.253761 4.58241C-0.0845873 4.32115 -0.0845871 3.67885 0.253761 3.41759L4.55759 0.0943168C4.90074 -0.170652 5.33333 0.154128 5.33333 0.676727L5.33333 7.32327C5.33333 7.84587 4.90074 8.17065 4.5576 7.90568L0.253761 4.58241Z" fill="#110E12"/></svg></button>
                <span class="calendar-title">2025</span>
                <button class="calendar-nav next"><svg width="6" height="8" viewBox="0 0 6 8" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M5.07949 4.58241C5.41784 4.32115 5.41784 3.67885 5.07949 3.41759L0.775656 0.0943172C0.432507 -0.170651 -8.18821e-05 0.154129 -8.18593e-05 0.676728L-8.15687e-05 7.32327C-8.15459e-05 7.84587 0.432507 8.17065 0.775657 7.90568L5.07949 4.58241Z" fill="#110E12"/></svg></button>
              </div>
              
              <div class="calendar-header-group">
                <button class="calendar-nav prev"><svg width="6" height="8" viewBox="0 0 6 8" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M0.253761 4.58241C-0.0845873 4.32115 -0.0845871 3.67885 0.253761 3.41759L4.55759 0.0943168C4.90074 -0.170652 5.33333 0.154128 5.33333 0.676727L5.33333 7.32327C5.33333 7.84587 4.90074 8.17065 4.5576 7.90568L0.253761 4.58241Z" fill="#110E12"/></svg></button>
                <span class="calendar-title">June</span>
                <button class="calendar-nav next"><svg width="6" height="8" viewBox="0 0 6 8" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M5.07949 4.58241C5.41784 4.32115 5.41784 3.67885 5.07949 3.41759L0.775656 0.0943172C0.432507 -0.170651 -8.18821e-05 0.154129 -8.18593e-05 0.676728L-8.15687e-05 7.32327C-8.15459e-05 7.84587 0.432507 8.17065 0.775657 7.90568L5.07949 4.58241Z" fill="#110E12"/></svg></button>
              </div>
            </div>

            <div class="calendar-widget__weekdays">
              <span>Mo</span><span>Tu</span><span>We</span><span>Th</span><span>Fr</span><span>Sa</span><span>Su</span>
            </div>
            
            <div class="calendar-widget__grid">
              <span class="day prev-month">30</span>
              <span class="day prev-month">31</span>
              <span class="day">1</span><span class="day">2</span><span class="day">3</span><span class="day">4</span><span class="day">5</span>
              <span class="day">6</span><span class="day">7</span><span class="day">8</span><span class="day">9</span><span class="day">10</span><span class="day">11</span><span class="day">12</span>
              <span class="day">13</span><span class="day">14</span>
              <span class="day selected start">15</span>
              <span class="day selected">16</span><span class="day selected">17</span><span class="day selected">18</span><span class="day selected">19</span>
              <span class="day selected">20</span><span class="day selected">21</span><span class="day selected">22</span><span class="day selected">23</span>
              <span class="day selected end">24</span>
              
              <span class="day">25</span><span class="day">26</span>
              <span class="day">27</span><span class="day">28</span><span class="day">29</span><span class="day">30</span>
              <span class="day next-month">1</span><span class="day next-month">2</span><span class="day next-month">3</span>
            </div>

            <div class="calendar-widget__footer">
               <button class="btn-clear" @click="closeModals">Clear all</button>
               <button class="btn-apply" @click="closeModals">Apply</button>
            </div>
         
         </div>
          </div>
        </div>
  
        <button class="recent__export">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M10.0001 12.0833V3.75M10.0001 12.0833C9.41658 12.0833 8.32636 10.4214 7.91675 10M10.0001 12.0833C10.5836 12.0833 11.6738 10.4214 12.0834 10" stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M16.6666 13.75C16.6666 15.8183 16.2349 16.25 14.1666 16.25H5.83325C3.76492 16.25 3.33325 15.8183 3.33325 13.75" stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
  
          Export PDF
        </button>
      </div>
  
      <div class="search-bar-row">
        <div class="search-input-wrap">
          <svg
            width="18"
            height="18"
            viewBox="0 0 24 24"
            fill="none"
            stroke="#9CA3AF"
            stroke-width="2"
          >
            <circle cx="11" cy="11" r="8"></circle>
            <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
          </svg>
  
          <input type="text" placeholder="Search policies, procedures" />
        </div>
  
        <div class="ai-assist">
          <button class="ai-assist-btn" ref="aiBtn" @click="toggleAiModal">AI Assistance</button>

          <div class="modal-ai-assist" v-if="isAiModalOpen" ref="aiModal">
            <div class="modal-ai-assist__inner" @click.stop>
              <button>GDPR compliance rules</button>
              <button>Remote work policy</button>
              <button>Overtime rules</button>
              <button @click="openChat">Other</button>
            </div>
          </div>
        </div>
      </div>
  
      <div class="search-list">
            <RecentItem v-for="item in items" :key="item.id" :item="item"/>
      </div>

    </div>
  </section>


    <div class="overlay" @click="onOverlayClick" v-if="isChatOpen">
      <div class="chat" @click.stop>
        <div class="chat__inner">
          <div class="chat__header"><button @click="closeChat"><svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M16.6655 16.6668L3.3335 3.3335M3.33492 16.6668L16.6668 3.3335" stroke="#110E12" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/></svg></button></div>
          <h3 class="chat__title-2">
            Chat with AI
          </h3>
          <div class="chat__box">
              <div class="chat__bot-title">How can I help you?</div>
          </div>
          <form class="chat__form">
            <input type="text" placeholder="Write your text" class="chat__input">
            <button class="chat__button">Send<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M9.935 3.9917C13.9136 2.63538 15.9028 1.95722 16.9728 3.02718C18.0427 4.09714 17.3646 6.08643 16.0083 10.065L15.0847 12.7743C14.0431 15.8298 13.5222 17.3576 12.6637 17.484C12.4329 17.518 12.194 17.4976 11.9656 17.4243C11.1162 17.1516 10.6672 15.5408 9.76925 12.3192C9.57008 11.6046 9.4705 11.2473 9.24366 10.9743C9.17783 10.8952 9.10483 10.8222 9.02566 10.7563C8.75275 10.5295 8.39541 10.4299 7.68087 10.2308C4.45926 9.33275 2.84845 8.88375 2.57575 8.03439C2.50243 7.80603 2.48197 7.56711 2.51596 7.33629C2.6424 6.47777 4.17016 5.95695 7.22566 4.91532L9.935 3.9917Z" stroke="white" stroke-width="1.5"/>
  </svg></button>
          </form>
        </div>
      </div>
    </div>
</template>
