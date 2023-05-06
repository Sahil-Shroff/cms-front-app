<script setup lang="ts">
import { onMounted } from 'vue';
import TabItem from './TabItem.vue'

const emit = defineEmits<{
    (e: 'tabSelected', tabName: Array<string>): void
}>();

const tabItems = ['1', '2', '3', '4'];
const tabMap = {1: ['a', 'b'], 2: ['c', 'd']};
const onTabSelected = (tabName) => {
    emit('tabSelected', tabMap[tabName]);
}

onMounted(() => { onTabSelected(tabItems[0]) });
</script>

<template>
    <div id="tab-menu">
        <tab-item
            v-for="tab in tabItems"
            :key="tab"
            :tab-name="tab"
            @tab-selected="onTabSelected"
        />
    </div>
</template>

<style scoped>
#tab-menu {
    background-color: #2934ff;
    border: 1px solid whitesmoke;
    height: 30px;
    align-content: center;
}
</style>