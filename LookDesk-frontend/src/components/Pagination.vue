<script setup>
import { computed } from "vue";

const props = defineProps({
  total: Number,          // всего результатов
  perPage: Number,        // сколько на странице
  currentPage: Number     // текущая страница
});

const emit = defineEmits(['update:currentPage']);

const totalPages = computed(() =>
  Math.ceil(props.total / props.perPage)
);

const start = computed(() =>
  (props.currentPage - 1) * props.perPage + 1
);

const visiblePages = computed(() => {
  const total = totalPages.value;
  const current = props.currentPage;
  const limit = props.perPage; // сколько страниц показывать

  // если страниц мало — показываем всё
  if (total <= limit) {
    return Array.from({ length: total }, (_, i) => i + 1);
  }

  let start = current - Math.floor(limit / 2);
  let end = current + Math.floor(limit / 2);

  // корректируем начало
  if (start < 1) {
    start = 1;
    end = limit;
  }

  // корректируем конец
  if (end > total) {
    end = total;
    start = total - limit + 1;
  }

  return Array.from({ length: end - start + 1 }, (_, i) => start + i);
});

const goTo = (page) => {
  emit("update:currentPage", page);
};
</script>


<template>
    <div class="pagination">
        <span class="pagination__info">
        Showing {{ start }} of {{ total }} results
        </span>
        <div class="pagination__switcher">
            <button class="pagination__arrow" :disabled="currentPage === 1" @click="goTo(currentPage - 1)">
            <svg width="12" height="12" viewBox="0 0 12 12" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M3.14574 5.64332C2.95142 5.83765 2.95142 6.16231 3.14574 6.35713L7.6295 10.8524C7.82631 11.0492 8.14549 11.0492 8.34181 10.8524C8.53863 10.6556 8.53863 10.3359 8.34181 10.1391L4.21424 6L8.34231 1.86142C8.53913 1.66411 8.53913 1.34493 8.34231 1.14761C8.14549 0.950796 7.82631 0.950796 7.62999 1.14761L3.14574 5.64332Z" fill="currentColor"/></svg>
            </button>
            <button v-for="page in visiblePages" :key="page" class="pagination__page" :class="{ active: page === currentPage }" @click="goTo(page)" v-if="page !== '...' ">
            {{ page }}
            </button>
            <span v-else class="pagination__dots">…</span>
            <button class="pagination__arrow" :disabled="currentPage === totalPages" @click="goTo(currentPage + 1)">
            <svg width="12" height="12" viewBox="0 0 12 12" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M8.85426 5.64332C9.04858 5.83765 9.04858 6.16231 8.85426 6.35713L4.3705 10.8524C4.17369 11.0492 3.85451 11.0492 3.65819 10.8524C3.46137 10.6556 3.46137 10.3359 3.65819 10.1391L7.78576 6L3.65769 1.86142C3.46087 1.66411 3.46087 1.34493 3.65769 1.14761C3.85451 0.950796 4.17369 0.950796 4.37001 1.14761L8.85426 5.64332Z" fill="currentColor"/></svg>
            </button>
        </div>
    </div>
</template>