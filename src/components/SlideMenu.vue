<script setup lang="ts">
import { ref } from 'vue';
import type { Ref } from 'vue';

const props = defineProps<{
    currentLeftPanel: Array<string>,
}>();

const emit = defineEmits<{
    (e: 'pageSelected', tabName: string): void
}>()

// const tabItemSpacing: Ref<string> = ref('5px');

</script>

<template>
    <div id="slide-menu">
        <div>
            <input type="text" />
        </div>
        <div v-for="page in currentLeftPanel">
            <button @click="emit('pageSelected', page)">
                {{ page }}
            </button>
        </div>
    </div>
</template>

<style scoped>
#slide-menu {
    background-color: aliceblue;
    float: left;
    min-width: 200px;
    min-height: 100%;
}
#slide-menu button {
    width: 200px;
    margin: 10px;
}
</style>