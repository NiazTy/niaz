<script setup lang="ts">
  useSeoMeta({
    title: 'About Me',
    description: 'Learn more about Muhammad Zakky Pusponegoro.',
  })

  const revealElements = ref<HTMLElement[]>([])
  const bgColor = ref('#ffffff')

  onMounted(() => {
    revealElements.value = Array.from(document.querySelectorAll<HTMLElement>('[data-reveal="about"]'))

    const revealObserver = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => entry.isIntersecting && entry.target.classList.add('reveal-active'))
      },
      { threshold: 0.25 }
    )

    revealElements.value.forEach((el) => revealObserver.observe(el))

    const sections = document.querySelectorAll<HTMLElement>('[data-bg]')

    const bgObserver = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) bgColor.value = entry.target.dataset.bg ?? '#ffffff'
        })
      },
      { threshold: 0.6 }
    )

    sections.forEach((sec) => bgObserver.observe(sec))
  })
</script>

<template>
  <div :style="{ backgroundColor: bgColor }" class="transition-colors duration-1000 ease-in-out">
    <!-- HERO -->
    <section data-bg="#ffffff" class="flex min-h-screen items-center px-4 sm:px-6 md:px-12">
      <div class="mx-auto max-w-6xl space-y-6">
        <h1 class="font-libre-baskerville text-4xl sm:text-5xl md:text-6xl text-[#98A1C4]" data-reveal="about">
          About me
        </h1>
        <p class="font-libre-baskerville text-xl sm:text-2xl text-[#98A1C4] opacity-80" data-reveal="about">
          Muhammad Zakky Pusponegoro
        </p>
        <p class="max-w-md text-sm sm:text-base text-[#98A1C4] opacity-60" data-reveal="about">
          A student, a learner, and someone who enjoys overthinking life a bit too much.
        </p>
        <div class="h-0.5 w-24 rounded-full bg-[#98A1C4]" data-reveal="about" />
      </div>
    </section>

    <!-- STORY 1 -->
    <section data-bg="#98A1C4" class="flex min-h-screen items-center px-4 sm:px-6 text-white">
      <div class="mx-auto max-w-4xl space-y-8 sm:space-y-10">
        <p class="story-text" data-reveal="about">
          Sekolah di SMAN 1 Mejayan bikin aku sadar kalau kehidupan SMA nggak seindah yang ditayangin di film.
        </p>
        <p class="story-text" data-reveal="about">
          Nggak ada kisah cinta manis atau petualangan seru — yang ada malah kayak filler anime yang pengen cepet-cepet diskip.
        </p>
        <p class="story-text font-semibold" data-reveal="about">
          Tapi ya, untungnya aku lumayan berprestasi.
        </p>
      </div>
    </section>

    <!-- QUOTE -->
    <section data-bg="#6F78A8" class="flex min-h-screen items-center justify-center px-4 text-white">
      <p class="max-w-3xl text-center font-libre-baskerville text-2xl sm:text-3xl md:text-4xl italic" data-reveal="about">
        “Dunia ini panggung sandiwara, jadi nikmati tiap momennya — bahkan saat lagi nyungsep.”
      </p>
    </section>

    <!-- STORY 2 -->
    <section data-bg="#98A1C4" class="flex min-h-screen items-center px-4 sm:px-6 text-white">
      <div class="mx-auto max-w-4xl space-y-8 sm:space-y-10">
        <p class="story-text" data-reveal="about">
          Dulu aku sering ngelakuin hal-hal nggak jelas dan nggak produktif.
        </p>
        <p class="story-text" data-reveal="about">
          Tapi sejak kenal dunia komputer dan logika, hidupku malah makin rumit.
        </p>
        <p class="story-text" data-reveal="about">
          Capek, nguras otak, bikin mikir — tapi entah kenapa tetap dijalanin.
        </p>
      </div>
    </section>

    <!-- INTEREST -->
    <section data-bg="#7F88B8" class="flex min-h-screen items-center justify-center px-4 text-white">
      <div class="space-y-4 text-center">
        <p class="text-base sm:text-lg opacity-80" data-reveal="about">
          Music, films, anime, series, books, and games.
        </p>
        <p class="text-sm opacity-60" data-reveal="about">
          Mostly J-Pop. Still emotionally stable. Probably.
        </p>
      </div>
    </section>

    <!-- WHAT I DO -->
    <section data-bg="#F5F6FA" class="flex min-h-screen items-center px-4 sm:px-6">
      <div class="mx-auto max-w-6xl space-y-12 sm:space-y-16">
        <h3 class="text-center font-libre-baskerville text-4xl sm:text-5xl md:text-6xl text-[#98A1C4]" data-reveal="about">
          Apa Yang Kulakukan?
        </h3>
        <div class="grid grid-cols-1 gap-6 sm:grid-cols-2 md:grid-cols-3">
          <div class="card" data-reveal="about">
            <h4>Belajar & Bereksperimen</h4>
            <p>Web, logika, dan hal-hal yang bikin otak panas tapi nagih.</p>
          </div>
          <div class="card" data-reveal="about">
            <h4>Menulis</h4>
            <p>Kadang teknis, kadang reflektif, kadang cuma curhat terselubung.</p>
          </div>
          <div class="card" data-reveal="about">
            <h4>Menikmati Hidup</h4>
            <p>Musik, film, anime, game — biar tetap waras.</p>
          </div>
        </div>
      </div>
    </section>

    <UiButtonSoundToggle />
  </div>
</template>
