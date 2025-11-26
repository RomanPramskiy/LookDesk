<script setup>
import { ref } from "vue";

const props = defineProps({
  item: {
    type: Object,
    required: true,
  },
});

const isOpen = ref(false);


const onOverlayClick = () => {
  isChatOpen.value = false
}

function toggleOpen() {
  isOpen.value = !isOpen.value;
}

const isFavorite = ref(false);

function toggleFavorite(e) {
  e.stopPropagation();
  isFavorite.value = !isFavorite.value;
}


const emit = defineEmits(["open"]);
</script>

<template>
  <div class="search-item" :class="{ active: isOpen }">
    <div class="search-item__head" @click="toggleOpen">
      <button class="star-icon">
        <svg @click.stop="toggleFavorite" width="22" height="22" viewBox="0 0 22 22" :fill="isFavorite ? '#110E12' : 'none'" xmlns="http://www.w3.org/2000/svg">
        <path d="M12.4791 2.19418L14.2389 5.74288C14.4789 6.23687 15.1188 6.7107 15.6588 6.80143L18.8484 7.33575C20.8882 7.67853 21.3682 9.1706 19.8983 10.6425L17.4186 13.1427C16.9986 13.5661 16.7687 14.3827 16.8986 14.9675L17.6086 18.0625C18.1685 20.5123 16.8786 21.46 14.7289 20.1796L11.7392 18.3952C11.1993 18.0726 10.3094 18.0726 9.75936 18.3952L6.76973 20.1796C4.62996 21.46 3.33011 20.5022 3.89005 18.0625L4.59997 14.9675C4.72995 14.3827 4.49998 13.5661 4.08002 13.1427L1.6003 10.6425C0.140464 9.1706 0.610414 7.67853 2.65018 7.33575L5.83983 6.80143C6.36977 6.7107 7.0097 6.23687 7.24967 5.74288L9.00946 2.19418C9.96936 0.268607 11.5292 0.268607 12.4791 2.19418Z" stroke="#110E12" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>

      <img :src="item.avatar" class="avatar" alt="avatar" />

      <div class="item-content">
        <span class="item-title">{{ item.title }}</span>

        <div class="item-meta">
          <span class="meta-user">{{ item.user }}</span>
          <span class="meta-dot"></span>
          <span class="meta-date">{{ item.date }}</span>
        </div>
      </div>

      <div class="status">
        <svg v-if="item.status === 'success'" width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M17 3.33782C15.5291 2.48697 13.8214 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22C17.5228 22 22 17.5228 22 12C22 11.3151 21.9311 10.6462 21.8 10" stroke="#00B07B" stroke-width="1.5" stroke-linecap="round"/><path d="M8 12.5C8 12.5 9.5 12.5 11.5 16C11.5 16 17.0588 6.83333 22 5" stroke="#00B07B" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
        <svg v-else-if="item.status === 'error'" width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22C17.5228 22 22 17.5228 22 12Z" stroke="#FF2D55" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/><path d="M14.9994 15L9 9M9.00064 15L15 9" stroke="#FF2D55" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
        <svg v-else width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22C17.5228 22 22 17.5228 22 12Z" stroke="#7A7482" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/><path d="M18.75 12.75H5.25" stroke="#7A7482" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
      </div>

      <div class="arrow">
        <svg class="triangle-icon"  :class="{ rotated: isOpen }" width="8" height="7" viewBox="0 0 8 7" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M7.8515 0.226157C7.75261 0.075344 7.63538 0 7.49994 0L0.500038 0C0.364534 0 0.247392 0.075344 0.148419 0.226157C0.0494455 0.377137 0 0.555636 0 0.761988C0 0.968298 0.0494455 1.1468 0.148419 1.29765L3.64838 6.63082C3.74746 6.78163 3.86461 6.85714 4 6.85714C4.13539 6.85714 4.25265 6.78163 4.35154 6.63082L7.8515 1.29761C7.95036 1.1468 8 0.968298 8 0.761946C8 0.555636 7.95036 0.377137 7.8515 0.226157Z" fill="#110E12"/>
        </svg>
      </div>
    </div>

    <div v-if="isOpen" class="search-item__body">
        <div class="ai-wrapper">
            <div class="ai-head">
              <span class="label">AI answer:</span>
              <span class="date">{{ item.aiAnswerDate }}</span>
            </div>
            <div class="ai-box">
      
              <p class="ai-text">{{ item.aiAnswer }}</p>
      
              <div class="ai-link"><button @click="emit('open')" href="#">Open Chat Details</button></div>
            </div>
        </div>

      <div class="comment-section" v-if="item.comment">
        <div class="ai-head">
          <span class="label">Comment:</span>

          <span class="date">{{ item.commentDate }}</span>
        </div>

        <p class="ai-text">{{ item.comment }}</p>
      </div>
    </div>
  </div>
</template>
