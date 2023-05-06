<script setup lang="ts">
import { ref } from 'vue';
import type { Ref } from 'vue';

const props = defineProps<{
    tabName: string,
}>();

const emit = defineEmits<{
    (e: 'tabSelected', tabName: string): void
}>()

const tabItemSpacing: Ref<string> = ref('5px');
</script>

<template>
  <div id="tab-item">
      <button @click="$emit('tabSelected', tabName)">
          {{ tabName }}
      </button>
  </div>
</template>

<style scoped>
#tab-item {
    background-color: inherit;
    float: left;
    padding: 0px v-bind(tabItemSpacing);
    border: 1px solid whitesmoke;
    border-bottom-width: 0px;
    border-top-width: 0px;
    height: inherit;
    text-align: center;
    align-content: center;
    font-family: Cambria;
    font-size: 18px;
    color: white;
}
button {
    background-color: inherit;
    border: none;
    height: inherit;
    color: inherit;
    font: inherit;
}
</style>