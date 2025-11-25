<script setup>
import { ref } from 'vue'

const activeItem = ref('procedures')

defineProps({
  open: Boolean
})
</script>

<template>
  <aside class="sidebar sidebar-desktop" :class="{ 'sidebar--open': open }">
    <div class="sidebar__inner">
      <div class="sidebar__search">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M11.6666 11.6665L14.6666 14.6665" stroke="#7A7482" stroke-linecap="round" stroke-linejoin="round"/><path d="M13.3334 7.3335C13.3334 4.01979 10.6471 1.3335 7.33337 1.3335C4.01967 1.3335 1.33337 4.01979 1.33337 7.3335C1.33337 10.6472 4.01967 13.3335 7.33337 13.3335C10.6471 13.3335 13.3334 10.6472 13.3334 7.3335Z" stroke="#7A7482" stroke-linejoin="round"/></svg>
        <input type="text" placeholder="Search policies, procedures" />
      </div>
      <div class="sidebar__group sidebar__links">
        <h3 class="sidebar__group-title">Pages</h3>
        <div class="sidebar__pages">
          <a href="/">Dashboard</a>
          <a href="/">Documents</a>
          <a href="/">Users</a>
          <a href="/">Belings</a>
        </div>
      </div>
      <div class="sidebar__group">
        <h3 class="sidebar__group-title">Categories</h3>
        <button class="sidebar__menu-item" :class="{ active: activeItem === 'policies' }" @click="activeItem = 'policies'">
          <div class="sidebar__item-content">
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M10 1.66666V2.66666C10 3.60946 10 4.08087 10.2929 4.37376C10.5858 4.66666 11.0572 4.66666 12 4.66666H13" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M2.66675 10.6667V5.33334C2.66675 3.44772 2.66675 2.50492 3.25253 1.91913C3.83832 1.33334 4.78113 1.33334 6.66675 1.33334H9.44782C9.72028 1.33334 9.85655 1.33334 9.97908 1.38409C10.1015 1.43484 10.1979 1.53118 10.3906 1.72387L12.9429 4.27615C13.1355 4.46884 13.2319 4.56518 13.2827 4.6877C13.3334 4.81021 13.3334 4.94646 13.3334 5.21896V10.6667C13.3334 12.5523 13.3334 13.4951 12.7476 14.0809C12.1618 14.6667 11.219 14.6667 9.33341 14.6667H6.66675C4.78113 14.6667 3.83832 14.6667 3.25253 14.0809C2.66675 13.4951 2.66675 12.5523 2.66675 10.6667Z" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M5.33325 7.33334H10.6666M5.33325 9.33334H10.6666M5.33325 11.3333H8.11379" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/></svg>
            <span class="sidebar__item-text">Policies<span class="sidebar__dot"></span>
            </span>
          </div>

          <span class="sidebar__item-count">24</span>
        </button>

        <button class="sidebar__menu-item" :class="{ active: activeItem === 'procedures' }" @click="activeItem = 'procedures'">
          <div class="sidebar__item-content">
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M7.3335 4H14.0002" stroke="#110E12" stroke-linecap="round"/><path d="M7.3335 8H14.0002" stroke="#110E12" stroke-linecap="round"/><path d="M7.3335 12H14.0002" stroke="#110E12" stroke-linecap="round"/><path d="M2 4.92853C2 4.92853 2.66667 5.36307 3 5.99996C3 5.99996 4 3.49996 5.33333 2.66663" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M2 12.2619C2 12.2619 2.66667 12.6965 3 13.3333C3 13.3333 4 10.8333 5.33333 10" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/></svg>
            <span class="sidebar__item-text">Procedures</span>
          </div>
          <span class="sidebar__item-count">18</span>
        </button>

        <button class="sidebar__menu-item" :class="{ active: activeItem === 'instruction' }" @click="activeItem = 'instruction'">
          <div class="sidebar__item-content">
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M10.3333 4.66663H5.66667M8.33267 7.33329H5.66602" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M13.3332 14.6667H3.99984C3.26346 14.6667 2.6665 14.0698 2.6665 13.3334M2.6665 13.3334C2.6665 12.597 3.26346 12 3.99984 12H13.3332V4.00004C13.3332 2.74296 13.3332 2.11442 12.9426 1.7239C12.5521 1.33337 11.9236 1.33337 10.6665 1.33337H6.6665C4.78088 1.33337 3.83808 1.33337 3.25229 1.91916C2.6665 2.50495 2.6665 3.44775 2.6665 5.33337V13.3334Z" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M13.0002 12C13.0002 12 12.3335 12.5085 12.3335 13.3333C12.3335 14.1581 13.0002 14.6667 13.0002 14.6667" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/></svg>
            <span class="sidebar__item-text">Instruction</span>
          </div>
          <span class="sidebar__item-count">31</span>
        </button>
      </div>
      <div class="sidebar__group">
        <h3 class="sidebar__group-title">Quick Actions</h3>
        <button class="sidebar__menu-item" :class="{ active: activeItem === 'add_document' }" @click="activeItem = 'add_document'">
          <div class="sidebar__item-content">
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M8.00049 4.5V11.501" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M11.501 8.00098H4.5" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/></svg>
            <span class="sidebar__item-text">Add Document</span>
          </div>
        </button>

        <button class="sidebar__menu-item" :class="{ active: activeItem === 'add_user' }" @click="activeItem = 'add_user'">
          <div class="sidebar__item-content">
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M10.0002 5.33333C10.0002 3.49239 8.50776 2 6.66683 2C4.82588 2 3.3335 3.49239 3.3335 5.33333C3.3335 7.17427 4.82588 8.66667 6.66683 8.66667C8.50776 8.66667 10.0002 7.17427 10.0002 5.33333Z" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M11.6668 14V9.33337M9.3335 11.6667H14.0002" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/><path d="M2 13.3333C2 10.756 4.08934 8.66663 6.66667 8.66663C7.65813 8.66663 8.57747 8.97583 9.33333 9.50309" stroke="#110E12" stroke-linecap="round" stroke-linejoin="round"/></svg>
            <span class="sidebar__item-text">Add User</span>
          </div>
        </button>
      </div>
    </div>
  </aside>
</template>
