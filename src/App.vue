<script setup lang="ts">
import { ref } from "vue";
import type { Ref } from "vue";
import Frame from './components/Frame.vue'
import Notification from "./components/Notification.vue";

const isVisible: Ref<boolean> = ref(false);
const notificationMesaage: Ref<string>  = ref('');

const onPageSelected = (page) => {
  notificationMesaage.value = page;
  isVisible.value = true;
}

</script>

<template>
  <Frame @page-selected="onPageSelected"/>
  <notification
    :is-visible="isVisible"
    :notification-mesaage="notificationMesaage"
    @close="() => {isVisible = false;}"
  />
</template>

<style scoped>

</style>
