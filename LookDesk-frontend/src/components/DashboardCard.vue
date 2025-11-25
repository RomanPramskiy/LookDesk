<script setup>
defineProps({
  title: String,
  value: String,
  subtitle: String,
  subtitle_value: String,
  icon: String,
  color_value: Boolean,
  button_active: Boolean
})
</script>


<template>
    <div class="card-stat">
        <div class="card-stat__inner">
            <div class="card-stat__info">
                <h4>{{ title }}</h4>
                <p>{{ value }}</p>
                <span :class="button_active ? 'header__active' : ''"><strong :class="color_value ? 'text-red' : 'text-green'">{{ subtitle_value }}</strong> {{ subtitle }}</span>
            </div>
            <div class="stat-card__icon" v-html="icon"></div>
        </div>
    </div>
</template>