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
            Notification
        </template>
        <template #content>
            Content
        </template>
        <template #footer>
            <button @click="emit('close')">
                OK
            </button>
        </template>
    </modal>
  </div>
</template>

<style scoped>
button {
    padding: 10px;
    padding-inline: 25px;
}
</style>