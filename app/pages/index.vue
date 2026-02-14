<script lang="ts" setup>
useSeoMeta({
  title: 'Home - Muhammad Zakky Pusponegoro',
  description: 'Halaman utama yang menampilkan informasi tentang Muhammad Zakky Pusponegoro, seorang pelajar yang tertarik di bidang kreatif dan kepenulisan. Temukan karya-karya visual, cerita, dan ide-ide kreatif yang bermakna.',
});
</script>

<template>
  <section class="min-h-screen bg-[#f8f6ee] flex items-center justify-center px-6 md:px-12">
    <div class="max-w-7xl w-full grid md:grid-cols-2 mt-40 mb-10 gap-12 items-center">
      <div class="space-y-6">
        <p class="text-lg font-semibold tracking-wide text-gray-700 fade-up">Halo! Saya</p>
        <h1 class="text-4xl md:text-6xl xl:text-7xl font-black leading-tight tracking-wide fade-up delay-100">
          MUHAMMAD <br />
          ZAKKY <br />
          PUSPONEGORO
        </h1>
        <p class="text-lg md:text-xl text-gray-600 max-w-lg leading-relaxed fade-up delay-200">
          Seorang <i>pelajar</i> dari SMAN 1 Mejayan yang tertarik di bidang <b>kreatif</b> dan <b>kepenulisan</b>.
          Saya senang membuat karya visual, cerita, dan ide yang bermakna.
        </p>
        <div class="flex gap-4 flex-wrap fade-up delay-300">
          <a href="#contact" class="bg-[#1a1b27] text-white px-8 py-3 rounded-full font-semibold shadow-lg hover:shadow-xl hover:-translate-y-1 transition duration-300">
            Hubungi Saya
          </a>
          <a href="/blog" download>
            <button class="border-2 border-[#1a1b27] hover:cursor-pointer text-[#1a1b27] px-8 py-3 rounded-full font-semibold hover:bg-[#1a1b27] hover:text-white transition duration-300">
              Blog Gwe
            </button>
          </a>
        </div>
      </div>
      <div class="fade-up delay-200">
        <div class="rounded-[2.5rem] overflow-hidden shadow-2xl hover:scale-[1.02] transition duration-500">
          <img src="/images/foto-aku.png" alt="profile" class="w-full h-112.5 md:h-150 object-cover" />
        </div>
      </div>
    </div>
  </section>
  <section class="bg-[#f8f6ee] py-28 px-6 md:px-16">
    <div class="max-w-5xl mx-auto text-center space-y-10">
      <h2 class="text-4xl font-black tracking-wide">
        Tentang Saya
      </h2>
      <p class="text-lg text-gray-600 leading-relaxed max-w-3xl mx-auto">
        Saya adalah pelajar yang tertarik pada dunia kreatif, kepenulisan, film, dan teknologi. Hidup bagi saya adalah panggung sandiwara — jalani saja, bahkan saat hidup terasa rumit.
      </p>
      <NuxtLink to="/about-me" class="inline-block bg-[#1a1b27] text-white px-8 py-3 rounded-full hover:-translate-y-1 hover:shadow-lg transition">
        Baca Selengkapnya
      </NuxtLink>
    </div>
  </section>
  <section class="bg-[#1a1b27] py-28 px-6 md:px-16 text-[#f8f6ee]">
    <div class="max-w-6xl mx-auto">
      <div class="text-center mb-20">
        <h2 class="text-4xl font-black tracking-wide">
          Hal yang Saya Kerjakan
        </h2>
        <p class="text-gray-400 mt-4">
          Banyak hal yang saya kerjakan, tapi ini beberapa karya yang paling saya banggakan. Saya percaya bahwa setiap karya adalah cerminan dari perjalanan dan proses kreatif yang unik.
        </p>
      </div>
      <div class="grid md:grid-cols-3 gap-8">
        <div class="bg-[#222334] rounded-3xl p-6 shadow-xl hover:-translate-y-2 hover:shadow-2xl transition duration-500">
          <h3 class="text-xl font-semibold mb-3">Film & Visual</h3>
          <p class="text-gray-400 text-sm mb-6">Saya sangat senang berkreasi dalam dunia visual dan sinematografi. Terlebih lagi ketika membuat sebuah karya yang memiliki pesan dan makna yang mendalam.</p>
        </div>
        <div class="bg-[#222334] rounded-3xl p-6 shadow-xl hover:-translate-y-2 hover:shadow-2xl transition duration-500">
          <h3 class="text-xl font-semibold mb-3">Writing</h3>
          <p class="text-gray-400 text-sm mb-6">Bagi saya, menulis tidak hanya sekadar menyampaikan ide yang terlintas, tetapi juga menjadi ruang untuk mengekspresikan perasaan dan refleksi pribadi. Tulisan menjadi jembatan antara pikiran dan dunia nyata.</p>
        </div>
        <div class="bg-[#222334] rounded-3xl p-6 shadow-xl hover:-translate-y-2 hover:shadow-2xl transition duration-500">
          <h3 class="text-xl font-semibold mb-3">Web Development</h3>
          <p class="text-gray-400 text-sm mb-6">Di dunia teknologi, saya menemukan kepuasan dalam menciptakan pengalaman digital yang menarik dan fungsional. Saya berfokus pada pengembangan web menggunakan teknologi modern.</p>
        </div>
      </div>
      <div class="text-center mt-16">
        <NuxtLink
          to="/portofolio"
          class="inline-block border border-[#f8f6ee] px-8 py-3 rounded-full hover:bg-[#f8f6ee] hover:text-[#1a1b27] transition">
          Lihat Semua Karya
        </NuxtLink>
      </div>
    </div>
  </section>
  <section id="contact" class="bg-[#f8f6ee] py-32 px-6 md:px-16">
    <div class="max-w-4xl mx-auto text-center space-y-10">
      <h2 class="text-4xl font-black tracking-wide">
        Mari Terhubung
      </h2>
      <p class="text-gray-600 text-lg leading-relaxed max-w-2xl mx-auto">
        Tertarik berdiskusi, berkolaborasi, atau sekadar berbagi cerita? Saya terbuka untuk percakapan tentang film, tulisan, teknologi, dan ide-ide kreatif lainnya.
      </p>
      <div class="flex justify-center gap-6 flex-wrap">
        <a
          href="mailto:hi@niaz.my.id"
          class="bg-[#1a1b27] text-white px-8 py-3 rounded-full hover:-translate-y-1 hover:shadow-lg transition">
          Kirim Email
        </a>
        <NuxtLink
          to="/portofolio"
          class="border border-[#1a1b27] text-[#1a1b27] px-8 py-3 rounded-full hover:bg-[#1a1b27] hover:text-white transition">
          Lihat Portfolio
        </NuxtLink>
      </div>
      <div class="flex justify-center gap-6 mt-8 text-[#1a1b27]">
        <a href="https://instagram.com/m.niazyk" target="_blank" class="hover:scale-110 transition">
          Instagram
        </a>
        <a href="https://github.com/NiazTy" target="_blank" class="hover:scale-110 transition">
          GitHub
        </a>
        <a href="https://www.linkedin.com/in/muhammad-zakky-pusponegoro-ab6579287/" target="_blank" class="hover:scale-110 transition">
          LinkedIn
        </a>
      </div>
    </div>
  </section>
</template>
