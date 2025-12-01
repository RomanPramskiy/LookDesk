<script setup>
import { ref } from 'vue'

import Header from "../components/Header.vue";
import Sidebar from "../components/Sidebar.vue";
import Hero from "../components/Hero.vue";
import DashboardStats from "../components/DashboardStats.vue";
import RecentSearches from "../components/RecentSearches.vue";
import TeamMembers from "../components/TeamMembers.vue";
import BillingSection from "../components/BillingSection.vue";
import ChatAi from '../components/ChatAi.vue';
import NotificationsPopUp from '../components/NotificationsPopUp.vue';

const sidebarOpen = ref(false)
const chatOpen = ref(false)
const NotificationsPopUpOpen = ref(false)

function onRecentOpen() {
  chatOpen.value = true
}

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
                <DashboardStats class="no-display-1440" />
                <ChatAi :open="chatOpen" @close="chatOpen = false"></ChatAi>
                <NotificationsPopUp :open="NotificationsPopUpOpen" @close="NotificationsPopUpOpen = false" v-if="NotificationsPopUpOpen" @open="onLearnMore"></NotificationsPopUp>
              </div>
              <div class="main-info-mobile">
                <DashboardStats />
                <div class="sidebars">
                  <TeamMembers />
                  <BillingSection />
                </div>
              </div>
              <div class="main-people" v-if="!chatOpen">
                <RecentSearches @open="onRecentOpen" />
                <div class="sidebars no-display-1440">
                  <TeamMembers />
                  <BillingSection />
                </div>
              </div>
            </div>

        </div>

      </div>
    </main>
  </div>
</template>
