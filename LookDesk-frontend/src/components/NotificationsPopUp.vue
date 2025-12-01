<script setup>
import { ref } from 'vue'
import Pagination from './Pagination.vue';

const checked = ref(false)
const page = ref(1);

const props = defineProps({
  open: {
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['close'])

function closeModal() {
  emit('close')
}
</script>

<template>
    <div class="notifications-popup" v-if="props.open">
      <div class="notifictaions-popup__inner">
        <div class="notifications-popup__header">
          <h2>Notifications</h2>
          <div class="notifications-modal__checkbox">
          <span class="notifications-modal__checkbox-label">{{ checked ? 'On' : 'Off' }}</span>
          <label class="toggle">
            <input type="checkbox" v-model="checked"></input>
              <span class="toggle-slider"></span>
            </label>
          </div>
        </div>
        <div class="notifications-popup__box">
          <div class="massage-left">
            <div class="message__inner">
                <h4>New document added</h4>
                <p>Qorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
                <span>2025-11-09, 08:24</span>
            </div>
            </div>
            <div class="massage-left">
            <div class="message__inner">
                <h4>New document added</h4>
                <p>Qorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
                <span>2025-11-09, 08:24</span>
            </div>
            </div>
            <div class="massage-left">
            <div class="message__inner">
                <h4>New document added</h4>
                <p>Qorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
                <span>2025-11-09, 08:24</span>
            </div>
            </div>
            <div class="massage-left">
            <div class="message__inner">
                <h4>New document added</h4>
                <p>Qorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
                <span>2025-11-09, 08:24</span>
            </div>
            </div>
            <div class="massage-left">
            <div class="message__inner">
                <h4>New document added</h4>
                <p>Qorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
                <span>2025-11-09, 08:24</span>
            </div>
            </div>
            <div class="massage-left">
            <div class="message__inner">
                <h4>New document added</h4>
                <p>Qorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
                <span>2025-11-09, 08:24</span>
            </div>
            </div>
            <div class="massage-left">
            <div class="message__inner">
                <h4>New document added</h4>
                <p>Qorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
                <span>2025-11-09, 08:24</span>
            </div>
            </div>
        </div>
        <div class="notifications-popup__pagination">
            <Pagination :total="14" :perPage="6" :currentPage="page" @update:currentPage="page = $event"/>
        </div>
        <div class="notifications-popup__close">
          <button @click="closeModal">Close</button>
        </div>
      </div>
    </div>
</template>