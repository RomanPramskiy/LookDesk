<script setup>
import { ref } from 'vue'

import Header from "../components/Header.vue";
import Sidebar from "../components/Sidebar.vue";
import Hero from "../components/Hero.vue";
import DashboardStats from "../components/DashboardStats.vue";
import RecentSearches from "../components/RecentSearches.vue";
import TeamMembers from "../components/TeamMembers.vue";
import BillingSection from "../components/BillingSection.vue";

const sidebarOpen = ref(false)
</script>

<template>
  <div class="wrapper">
    <Header @toggleSidebar="sidebarOpen = !sidebarOpen"></Header>
    <main class="main">
      <div class="container">
        <div class="main-layout">
            <Sidebar :open="sidebarOpen"></Sidebar>
            <div class="main-content">
              <div class="main-info">
                <Hero></Hero>
                <DashboardStats class="no-display-1440" />
              </div>
              <div class="main-info-mobile">
                <DashboardStats />
                <div class="sidebars">
                  <TeamMembers />
                  <BillingSection />
                </div>
              </div>
              <div class="main-people">
                <RecentSearches />
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
