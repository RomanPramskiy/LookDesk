<script setup>
import { ref } from 'vue'

import Header from '../components/Header.vue';
import Sidebar from "../components/Sidebar.vue";
import Hero from "../components/Hero.vue";
import DocumentsRegistry from '../components/DocumentsRegistry.vue';
import DocumentDetails from '../components/DocumentDetails.vue';
import DocumentStats from '../components/DocumentStats.vue';
import NotificationsPopUp from '../components/NotificationsPopUp.vue';

const sidebarOpen = ref(false)
const NotificationsPopUpOpen = ref(false)

function onNotificationsOpen() {
 NotificationsPopUpOpen.value = true
}

const onLearnMore = () => {
  NotificationsPopUpOpen.value = false
}
</script>

<template>
    <div class="wrapper">
        <Header @toggleSidebar="sidebarOpen = !sidebarOpen" @open="onNotificationsOpen"></Header>
        <main class="main">
          <div class="container">
            <div class="main-layout">
                <Sidebar :open="sidebarOpen"></Sidebar>
                <div class="main-content">
                  <div class="main-info">
                    <Hero></Hero>
                    <NotificationsPopUp :open="NotificationsPopUpOpen" @close="NotificationsPopUpOpen = false" v-if="NotificationsPopUpOpen" @open="onLearnMore"></NotificationsPopUp>
                  </div>
                  <div class="main-info-mobile main-info-mobile-documents">
                    <div class="sidebars sidebars-document">
                      <DocumentDetails />
                      <DocumentStats />
                    </div>
                  </div>
                  <div class="main-people" v-if="!chatOpen">
                    <DocumentsRegistry />
                    <div class="sidebars sidebars-document no-display-1440">
                      <DocumentDetails />
                      <DocumentStats />
                    </div>
                  </div>
                </div>
            </div>
          </div>
        </main>
    </div>
</template>