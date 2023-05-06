<script setup lang="ts">
import { ref } from 'vue';

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
  <div v-show="isVisible" class="modal-overlay">
    <div class="modal-main">
        <div id="header">
            <slot name="header">
                Modal title
            </slot>
        </div>
        <div id="content">
            <slot name="content">
                default content
            </slot>
        </div>
        <div id="footer">
            <slot name="footer">
                <button @click="emit('close')">
                    OK
                </button>
            </slot>
        </div>
    </div>
</div>
</template>

<style scoped>
.modal-overlay {
  z-index: 1;
  display: flex;
  position: absolute;
  top: 0px;
  bottom: 0px;
  left: 0px;
  right: 0px;
  width: 100%;
  height: 100%;
  align-content: center;
  background-color: rgba(0, 0, 0, 0.211);
}

.modal-main {
  padding: 10px;
  margin: 100px;
  align-content: center;
  background-color: white;
  border: solid;
}
</style>