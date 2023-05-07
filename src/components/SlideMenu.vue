<script setup lang="ts">
import { ref } from 'vue';
import type { Ref } from 'vue';

const props = defineProps<{
    currentLeftPanel: Array<string>,
}>();

const emit = defineEmits<{
    (e: 'pageSelected', page: string): void
}>();

// const tabItemSpacing: Ref<string> = ref('5px');

</script>

<template>
    <div id="slide-menu">
        <div id="search-bar">
            <input type="text" />
        </div>
        <div
            v-for="(page, index) in currentLeftPanel"
            :key="index" 
            id="slide-menu-item"
            @click="emit('pageSelected', page)"
        >
            {{ page }}
        </div>
    </div>
</template>

<style scoped>
#search-bar {
    margin: 10px;
}

#search-bar input {
    width: 100%;
}

#slide-menu {
    background-color: aliceblue;
    border: 1px solid;
    float: left;
    width: 200px;
    max-width: 100%;
    min-height: 100%;
}
#slide-menu-item {
    background-color: white;
    border: 1px solid;
    border-inline: none;
    width: 200px;
    max-width: 100%;
    padding: 5px;
    padding-inline: 10px;
}
#slide-menu-item:nth-child(2n+1) {
    border-top: none;
}
</style>