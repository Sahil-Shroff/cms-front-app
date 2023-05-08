<script setup lang="ts">
import { onMounted } from 'vue';
import TabItem from './TabItem.vue'

const emit = defineEmits<{
    (e: 'tabSelected', tabName: Array<string>): void
}>();

const tabItems: string[] = Array.from(Array<string>(5), (_, index) => 'tab ' + (index + 1));
const tabMap = Object.fromEntries(
    tabItems.map(tabItem => [tabItem, Array.from(Array<string>(5), (_, index) => tabItem + ' ' + (index + 1))])
);
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