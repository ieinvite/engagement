<template>
  <div class="app-container">
    <audio ref="music" loop>
      <source src="/music/music.mp3" type="audio/mp3" />
    </audio>

    <Transition name="cinematic">
      <IntroScreen v-if="showIntro" key="intro" class="screen" @finished="enterSite" />

      <Invitation v-else key="invitation" class="screen" />
    </Transition>

    <Button
      class="music-button"
      icon="pi pi-volume-up"
      rounded
      severity="primary"
      variant="text"
      @click="toggleMusic"
    />
  </div>
</template>

<script setup>
  import { onMounted, ref } from 'vue'
  import IntroScreen from './components/IntroScreen.vue'
  import Invitation from './components/Invitation.vue'

  const showIntro = ref(true)
  const music = ref(null)
  const isPlaying = ref(false)

  onMounted(() => {
    document.addEventListener(
      'click',
      () => {
        music.value.play()
        isPlaying.value = true
      },
      { once: true },
    )
  })

  const toggleMusic = () => {
    if (!isPlaying.value) {
      music.value.play()
      isPlaying.value = true
    } else {
      music.value.pause()
      isPlaying.value = false
    }
  }

  const enterSite = () => {
    showIntro.value = false
    window.scrollTo(0, 0)
  }
</script>

<style scoped>
  .app-container {
    position: relative;
    width: 100%;
    min-height: 100vh;
    overflow-x: hidden;
  }

  .screen {
    position: absolute;
    width: 100%;
    top: 0;
    left: 0;
  }

  .music-button {
    position: fixed;
    bottom: 20px;
    right: 20px;
    z-index: 30;
  }

  :deep(.p-button-text:not(:disabled):hover) {
    background: rgba(255, 255, 255, 0.2);
    border-color: white;
    color: white;
  }

  :deep(.p-button-text) {
    color: #eeeeee !important;
  }

  .cinematic-enter-active,
  .cinematic-leave-active {
    transition:
      opacity 1.4s cubic-bezier(0.77, 0, 0.18, 1),
      transform 1.4s cubic-bezier(0.77, 0, 0.18, 1),
      filter 1.4s cubic-bezier(0.77, 0, 0.18, 1);
  }

  .cinematic-enter-from {
    opacity: 0;
    transform: scale(1.05);
    filter: blur(15px);
    z-index: 2;
  }

  .cinematic-enter-to {
    opacity: 1;
    transform: scale(1);
    filter: blur(0);
    z-index: 2;
  }

  .cinematic-leave-from {
    opacity: 1;
    transform: scale(1);
    filter: blur(0);
    z-index: 1;
  }

  .cinematic-leave-to {
    opacity: 0;
    transform: scale(0.95);
    filter: blur(10px);
    z-index: 1;
  }
</style>