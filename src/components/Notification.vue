<script setup lang="ts">
import { ref } from 'vue';
import Modal from "./Modal.vue";

const emit = defineEmits<{
    (e: 'close'): void
}>();

withDefaults(defineProps<{
        isVisible: boolean
    }>(), {
        isVisible: () => false
});

</script>

<template>
  <div id="notification">
    <modal :is-visible="isVisible" @close="emit('close')">
        <template #header>
            <div id="header">
                <h1>Notification</h1>
            </div>
        </template>
        <template #content>
            <div id="content">
                Content
            </div>
        </template>
        <template #footer>
            <div id="footer">
                <button @click="emit('close')">
                    OK
                </button>
            </div>
        </template>
    </modal>
  </div>
</template>

<style scoped>
#header {

}
</style>