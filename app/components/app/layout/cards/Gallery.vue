<script setup lang="ts">
const images = ref([
  '/images/photograph/IMG_0056.webp',
  '/images/photograph/IMG_6905.webp',
  '/images/photograph/IMG_6938.webp',
  '/images/photograph/IMG_7209.webp',
  '/images/photograph/IMG_0065.webp',
  '/images/photograph/IMG_7289.webp',
])

const STEP = 6
const visibleCount = ref(STEP)
const selectedIndex = ref<number | null>(null)

const openImage = (index: number) => {
  selectedIndex.value = index
}

const closeImage = () => {
  selectedIndex.value = null
}

const nextImage = () => {
  if (selectedIndex.value === null) return
  selectedIndex.value =
    (selectedIndex.value + 1) % images.value.length
}

const prevImage = () => {
  if (selectedIndex.value === null) return
  selectedIndex.value =
    (selectedIndex.value - 1 + images.value.length) %
    images.value.length
}

const loadMore = () => {
  visibleCount.value = Math.min(
    visibleCount.value + STEP,
    images.value.length
  )
}

const canLoadMore = computed(() => {
  return visibleCount.value < images.value.length
})

const showEnding = ref(false)

watch(canLoadMore, (val) => {
  if (!val) {
    setTimeout(() => {
      showEnding.value = true
    }, 600)
  }
})

onMounted(() => {
  window.addEventListener('keydown', (e) => {
    if (selectedIndex.value === null) return
    if (e.key === 'Escape') closeImage()
    if (e.key === 'ArrowRight') nextImage()
    if (e.key === 'ArrowLeft') prevImage()
  })
})
</script>

<template>
    <div class="grid py-6 grid-cols-2 md:grid-cols-3 gap-2 md:gap-4 md:px-12">
    <div
      v-for="(img, index) in images.slice(0, visibleCount)"
      :key="img"
      class="group cursor-pointer overflow-hidden rounded-md"
      @click="openImage(index)"
    >
      <img
        :src="img"
        loading="lazy"
        class="w-full h-full object-cover
               transition-transform duration-700
               group-hover:scale-105"
        alt="Memories"
      />
    </div>
  </div>
  <transition name="button-fade">
    <div
      v-if="canLoadMore"
      class="flex justify-center my-24"
    >
      <button
        @click="loadMore"
        class="group relative px-10 py-3
               font-spectral text-sm tracking-widest
               border-b border-[#98A1C4]
               transition-all duration-300
               hover:-translate-y-1 hover:cursor-pointer
               active:scale-95"
      >
        <span class="relative z-10">
          Load more memories
        </span>

        <span
          class="absolute left-1/2 bottom-1
                 w-0 h-px bg-[#98A1C4]
                 transition-all duration-500
                 group-hover:w-3/4
                 -translate-x-1/2"
        ></span>
      </button>
    </div>
  </transition>

  <transition name="ending-dramatic">
    <div
      v-if="showEnding"
      key="ending"
      class="my-24 text-center font-spectral
             text-sm tracking-[0.3em]
             text-[#98A1C4]/60"
    >
      That’s all for now.
    </div>
  </transition>

  <div
    v-if="selectedIndex !== null"
    class="fixed inset-0 z-50 bg-black/80
           flex items-center justify-center"
    @click.self="closeImage"
  >
    <button
      class="absolute top-6 right-6 hover:cursor-pointer text-white text-xl"
      @click="closeImage"
    >
      <img src="/icon/close.svg" alt="close" class="w-6 h-6"/>
    </button>

    <button
      class="absolute left-6 text-white hover:cursor-pointer text-2xl"
      @click.stop="prevImage"
    >
      <img src="/icon/arrow-back.svg" alt="arrow back" class="w-6 h-6"/>
    </button>

    <img
      :src="images[selectedIndex]"
      class="max-h-[85vh] max-w-[90vw] rounded-lg
             transition-all duration-500"
      alt="Expanded"
    />

    <button class="absolute right-6 hover:cursor-pointer text-white text-2xl" @click.stop="nextImage">
      <img src="/icon/arrow-forward.svg" alt="arrow forward" class="w-6 h-6"/>
    </button>
  </div>
</template>