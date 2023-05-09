<script setup lang="ts">
import { computed, ref } from 'vue';
import type { Ref } from 'vue';

const props = defineProps<{
    currentLeftPanel: Array<string>,
}>();

const emit = defineEmits<{
    (e: 'pageSelected', page: string): void
}>();


const searchValue: Ref<string> = ref('');
const selectedLeftMenu = ref(props.currentLeftPanel);
const filteredCurrentLeftPanel = computed(() => selectedLeftMenu.value.filter((val) => val.toLowerCase().includes(searchValue.value) || searchValue.value === ''));

// const tabItemSpacing: Ref<string> = ref('5px');

</script>

<template>
    <div id="slide-menu">
        <div id="search-bar">
            <input type="text" v-model="searchValue"/>
        </div>
        <div
            v-for="(page, index) in filteredCurrentLeftPanel"
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
    max-width: 100%;
}

#search-bar input {
    background: white url("../assets/search-icon.svg") no-repeat 1px center;
    background-size: 14px 14px;
    border-radius: 10px;
    padding: 4px;
    padding-left: 9%;
    max-width: 70%;
}

#slide-menu {
    display: flex;
    flex-direction: column;
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