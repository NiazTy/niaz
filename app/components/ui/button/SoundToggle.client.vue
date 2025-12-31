<script setup lang="ts">
const ambience = ref<HTMLAudioElement | null>(null)
const isPlaying = ref(false)

const initAmbience = () => {
  if (ambience.value) return

  ambience.value = new Audio('/audio/sound.mp3')
  ambience.value.loop = true
  ambience.value.volume = 0.15
}

const toggleSound = async () => {
  if (!ambience.value) {
    initAmbience()
  }

  if (!ambience.value) return

  if (isPlaying.value) {
    ambience.value.pause()
    isPlaying.value = false
  } else {
    try {
      await ambience.value.play()
      isPlaying.value = true
    } catch (e) {
      console.warn('Audio play blocked by browser')
    }
  }
}

onMounted(() => {
  window.addEventListener(
    'click',
    () => {
      initAmbience()
    },
    { once: true }
  )
})

const router = useRouter()

router.beforeEach(() => {
  if (ambience.value) {
    ambience.value.pause()
    ambience.value.currentTime = 0
    ambience.value = null
    isPlaying.value = false
  }
})

</script>

<template>
    <button @click="toggleSound" class="fixed bottom-6 right-6 z-50 text-xs px-4 py-2 rounded-full bg-black/70 text-white backdrop-blur hover:bg-black transition"> 
        {{ isPlaying ? 'Sound Off' : 'Sound On' }}
    </button>
</template>