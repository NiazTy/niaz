<script setup lang="ts">
useSeoMeta({
    title: 'Gallery Page',
    description: 'Welcome to the gallery page of our application.',
  });
</script>

<template>
  <section class="z-10 pt-36">
  <div class="flex flex-col mt-16 mb-16 font-display space-y-4 md:mx-12">
    <h1 class="text-4xl md:text-5xl text-[#98A1C4] tracking-tight leading-tight">
      MEMBAWA <span class="text-[#676856]">KENANGAN</span> <br class="hidden md:block" />SEAKAN BARU TERJADI
    </h1>

    <p class="text-lg md:text-xl font-light font-displa text-[#98A1C4]/70 max-w-2xl">
      ENTAH ITU NYATA, <span class="text-[#676856]">ATAU HANYA TERSISA DI INGATAN</span>
    </p>
  </div>
  <AppLayoutCardsGallery />
</section>
</template>
