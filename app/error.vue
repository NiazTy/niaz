<script setup lang="ts">
const props = defineProps<{
  error: {
    statusCode: number
    statusMessage: string
  }
}>()

const handleError = () => {
  clearError({ redirect: '/' })
}
</script>

<template>
  <div class="min-h-screen bg-[#f8f6ee] flex items-center justify-center px-6">
    <div class="text-center max-w-2xl">
      <h1 class="text-[120px] md:text-[180px] font-black text-[#1a1b27] leading-none tracking-tight">
        {{ error.statusCode }}
      </h1>

      <h2 class="text-3xl md:text-4xl font-bold text-[#1a1b27] mb-6">
        Halaman Tidak Ditemukan
      </h2>

      <p class="text-gray-600 text-lg mb-12 leading-relaxed">
        Sepertinya halaman yang kamu cari tidak ada. Tapi tenang, seperti hidup — kadang tersesat itu bagian dari perjalanan.
      </p>

      <div class="flex justify-center gap-6 flex-wrap">
        <button
          @click="handleError"
          class="bg-[#1a1b27] text-white px-8 py-3 rounded-full
                 hover:-translate-y-1 hover:shadow-lg transition"
        >
          Kembali ke Beranda
        </button>

        <NuxtLink
          to="/blog"
          class="border border-[#1a1b27] text-[#1a1b27]
                 px-8 py-3 rounded-full
                 hover:bg-[#1a1b27] hover:text-white
                 transition"
        >
          Baca Blog
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<style scoped>
h1 {
  animation: fadeUp 1s ease forwards;
  opacity: 0;
}

@keyframes fadeUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
  from {
    opacity: 0;
    transform: translateY(40px);
  }
}
</style>