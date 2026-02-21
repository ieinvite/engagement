<template>
  <div class="intro" @click="start">
    <video
        ref="video"
        class="video"
        playsinline
        src="/video/intro.mp4"
    />

    <div v-if="!started" class="overlay">
      <h2>Davetiyeyi açmak için tıklayın</h2>
    </div>
  </div>
</template>

<script setup>
import {nextTick, ref} from 'vue';

const emit = defineEmits(['finished']);

const video = ref(null);
const started = ref(false);

const start = async () => {
  started.value = true;
  await nextTick();
  if (!video.value) return;
  video.value.play();
  video.value.onended = () => {
    emit('finished');
  };
}

</script>

<style scoped>
.intro {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  z-index: 10;
}

.video {
  position: absolute;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.overlay {
  position: relative;
  z-index: 3;
  color: #9A8B79;
  text-align: center;
  margin-top: 500px;
  font-size: 14px;
}
</style>
