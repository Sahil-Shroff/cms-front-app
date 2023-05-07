<script setup lang="ts">
import { ref } from 'vue';
import Page from './Page.vue';
import SlideMenu from './SlideMenu.vue';
import TabMenu from './TabMenu.vue'

const emit = defineEmits<{
    (e: 'pageSelected', page: string): void
}>();

const currentLeftPanel = ref(['']);
const currentPage = ref([]);

const onPageSelected = (page) => {
  currentPage.value = page;
  emit('pageSelected', page);
}
</script>

<template>
  <div id="frame">
    <slide-menu
      :current-left-panel="currentLeftPanel"
      @page-selected="onPageSelected"
    />
    <div id="container">
      <tab-menu
        @tab-selected="(value) => {currentLeftPanel = value}"
      />
      <page>
        
      </page>
    </div>
  </div>
</template>

<style scoped>
#frame {
  display: flex;
}
</style>