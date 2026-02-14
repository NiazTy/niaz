<script lang="ts" setup>
import { portfolioData } from "@/data/portfolioData";

const quotes = [
  "Dunia ini panggung sandiwara, jadi nikmati tiap momennya.",
  "Hidup bukan soal seberapa cepat kita sukses, tapi seberapa kuat kita bertahan.",
  "Logika memang melelahkan, tapi di sanalah pikiranku diasah.",
  "Cerita adalah cara manusia memahami dunia."
];

const currentQuote = ref(0);

let interval: ReturnType<typeof setInterval>;

onMounted(() => {
  interval = setInterval(() => {
    currentQuote.value =
      (currentQuote.value + 1) % quotes.length;
  }, 5000);
});

onUnmounted(() => {
  clearInterval(interval);
});


const activeSection = ref(portfolioData[0]?.id ?? "");

const scrollTo = (id: string) => {
  const el = document.getElementById(id);
  if (!el) return;

  el.scrollIntoView({
    behavior: "smooth",
    block: "start",
  });
};

const handleScroll = () => {
  let current = portfolioData[0]?.id ?? "";

  portfolioData.forEach((sec) => {
    const el = document.getElementById(sec.id);
    if (!el) return;

    const top = el.offsetTop - 150;
    if (window.scrollY >= top) {
      current = sec.id;
    }
  });

  activeSection.value = current;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<template>
    <section class="bg-[#f8f6ee]">
      <div id="header-about" class="flex pt-52 pb-16 px-8 lg:px-0 md:justify-around">
          <div class="flex flex-col">
              <h1 class="text-6xl font-snpro text-paragraph">PORTOFOLIO</h1>
              <p class="text-2xl font-snpro text-paragraph">MUHAMMAD ZAKKY PUSPONEGORO</p>
              <div class="w-1/2 mt-4 border-2 border-paragraph rounded-2xl"></div>
          </div>
          <div></div>
      </div>
  </section>
  <section class="relative">
    <div class="wave-container"></div>
  </section>
  <section class="bg-[#1a1b27] min-h-screen px-6 md:px-16 py-28">
    <div class="max-w-7xl mx-auto grid md:grid-cols-[250px_1fr] gap-16">
      <aside class="hidden md:block sticky top-32 h-fit">
        <div class="space-y-6">
          <h2 class="text-xl font-bold text-[#f8f6ee]">Portfolio</h2>
          <ul class="space-y-4">
            <li v-for="sec in portfolioData" :key="sec.id">
              <button
                @click="scrollTo(sec.id)"
                class="transition text-left"
                :class="activeSection === sec.id
                  ? 'text-[#f8f6ee] font-semibold'
                  : 'text-gray-500 hover:text-black'"
              >
                {{ sec.category }}
              </button>
            </li>
          </ul>
        </div>
      </aside>   
      <div class="space-y-32">
        <section v-for="sec in portfolioData" :key="sec.id" :id="sec.id">
          <h3 class="text-4xl font-black text-[#f8f6ee] mb-12">{{ sec.category }}</h3>
          <div class="grid md:grid-cols-2 gap-8">
            <div
                v-for="item in sec.items"
                :key="item.title"
                class="bg-[#222334] rounded-3xl p-6 shadow-xl hover:-translate-y-2 hover:shadow-2xl transition duration-500 flex flex-col">
                <img :src="item.image" class="w-full h-56 object-cover rounded-2xl mb-6" />
                <h4 class="text-xl font-semibold text-[#f8f6ee] mb-2">
                    {{ item.title }}
                </h4>
                <p class="text-gray-400 text-sm mb-6 flex-1">
                    {{ item.desc }}
                </p>
                <a
                    v-if="item.link"
                    :href="item.link"
                    target="_blank"
                    class="inline-block text-center bg-[#f8f6ee] text-[#1a1b27] py-2 px-6 rounded-full hover:bg-white transition font-semibold">
                    {{ item.linkLabel || "Lihat Proyek" }}
                </a>
                </div>
          </div>
        </section>
      </div>
    </div>
  </section>
  <section class="bg-[#f8f6ee] max-h-4xl my-auto py-32 px-6">
  <div class="flex flex-col items-center text-center space-y-16">
        <h2 class="text-4xl font-black tracking-wide">Quotes & Reflections</h2>
        <div class="relative">
            <transition name="fade" mode="out-in">
                <blockquote
                :key="currentQuote"
                class="text-2xl md:text-3xl font-semibold text-[#1a1b27] leading-relaxed">
                “{{ quotes[currentQuote] }}”
                </blockquote>
            </transition>
        </div>
        <div class="flex justify-center gap-3">
            <button
                v-for="(q, i) in quotes"
                :key="i"
                @click="currentQuote = i"
                class="w-3 h-3 rounded-full transition"
                :class="currentQuote === i
                ? 'bg-[#1a1b27]'
                : 'bg-gray-300'"
            />
        </div>
    </div>
</section>
</template>
