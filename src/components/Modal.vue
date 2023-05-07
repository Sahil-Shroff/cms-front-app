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
            <button @click="emit('close')">
                X
            </button>
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
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    height: fit-content;
    align-content: center;
    background-color: white;
    border: 1px solid;
}

#header {
    display: flex;
    background-color: rgb(0, 157, 255);
    padding: 5px;
    padding-inline: 200px;
    font-size: 45px;
    font-weight: 100;
}

#header button {
    margin: 5px;
    position: fixed;
    right: 1%;
    top: -2%;
    color: white;
    background-color: inherit;
    border: none;
    font-size: 30px;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

#header button:hover {
    background-color: rgb(0, 136, 255);
}

#content {
    padding: 40px;
    font-size: 20px;
}

#footer {
    padding: 10px;
    padding-inline: 200px;
}

#footer button {
    padding: 10px;
    padding-inline: 25px;
    background-color: white;
}
</style>