<script setup lang="ts">
import { ref } from 'vue';
const isHidden = ref(true);
const videoRef = ref<HTMLVideoElement | null>(null);

const handleHide = () => {
    isHidden.value = !isHidden.value;
    videoRef.value?.play();
}

</script>

<template>
    <div v-if="isHidden">
        <h1>Byrons Blog</h1>
        <p>Click <em>open</em> to begin.</p>
        <button @click="handleHide" class="btn btn-primary">Open</button>
    </div>
    <div v-if="!isHidden">
        <video ref="videoRef" class="vid" autoplay loop controls>
            <source src="./assets/rickroll.mp4" type="video/mp4">
            Sorry, your browser doesn't support embedded videos.
        </video>
    </div>
</template>

<style scoped>
div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

button {
    border-radius: 5px;
    font-size: x-large;
    color: var(--bb-black);
    background-color: var(--bb-old-gold);
    border-color: transparent;
}

video {
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    position: absolute;
}
</style>
