<script setup lang="ts">
import { ref } from 'vue';
import Page from './Page.vue';
import SlideMenu from './SlideMenu.vue';
import TabMenu from './TabMenu.vue'
import Notification from "./Notification.vue";


const currentLeftPanel = ref(['']);
const currentPage = ref('');
</script>

<template>
  <div id="frame">
    <slide-menu
      :current-left-panel="currentLeftPanel"
      @page-selected="(page) => {currentPage = page}"
    />
    <div id="container">
      <tab-menu
        @tab-selected="(value) => {currentLeftPanel = value}"
      />
      <page>
        
      </page>
    </div>
    <notification :is-visible="true" />
  </div>
</template>

<style scoped>
#frame {
  display: flex;
}
</style>