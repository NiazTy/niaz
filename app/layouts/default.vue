<script setup lang="ts">
    const isOpen = ref(false)

    const toggleMenu = () => { isOpen.value = !isOpen.value }
    const closeMenu  = () => { isOpen.value = false }
</script>
<template>
    <nav class="fixed font-display text-[#98A1C4] w-full z-20 overflow-hidden bg-white  shadow">
        <div class="flex justify-between items-center px-4 lg:px-16 py-9">
            <NuxtLink to="/">
                <div class="font-bold flex flex-col text-paragraph">
                    <p>PLACE FOR NIAZ</p>
                    <p class="font-semibold">HIGH SCHOOL STUDENT</p>
                </div>
            </NuxtLink>
            <!-- Desktop Menu -->
            <div class="hidden md:flex space-x-8">
                <NuxtLink to="/about-me" class="text-paragraph font-semibold">
                    ABOUT ME
                </NuxtLink>
                <NuxtLink to="/gallery" class="text-paragraph font-semibold">
                    GALLERY
                </NuxtLink>
                <NuxtLink to="/work" class="text-paragraph font-semibold">
                    WORK
                </NuxtLink>
                <NuxtLink to="/blog" class="text-paragraph font-semibold">
                    BLOG
                </NuxtLink>
            </div>
            <!-- HAMBURGER -->
            <button aria-label="Toggle navigation" class="flex flex-col gap-1.5 md:hidden" @click="toggleMenu">
                <span class="h-0.5 w-6 bg-current transition" :class="isOpen && 'translate-y-2 rotate-45'" />
                <span class="h-0.5 w-6 bg-current transition" :class="isOpen && 'opacity-0'" />
                <span class="h-0.5 w-6 bg-current transition" :class="isOpen && '-translate-y-2 -rotate-45'" />
            </button>
        </div>
        <transition name="fade-slide">
            <div v-if="isOpen" class="space-y-5 border-t bg-white px-6 py-6 md:hidden">
                <NuxtLink to="/about-me" class="block font-semibold" @click="closeMenu">ABOUT ME</NuxtLink>
                <NuxtLink to="/gallery" class="block font-semibold" @click="closeMenu">GALLERY</NuxtLink>
                <NuxtLink to="/work" class="block font-semibold" @click="closeMenu">WORK</NuxtLink>
                <NuxtLink to="/blog" class="block font-semibold" @click="closeMenu">BLOG</NuxtLink>
            </div>
        </transition>
    </nav>
    <slot />
    <footer>
        <div class="flex min-h-37.5 flex-col items-center justify-center space-y-4 border-t px-4 text-center text-[#98A1C4]">
            <p class="text-sm opacity-70">© 2025 Niazty. All rights reserved.</p>
            <div class="flex gap-6 text-sm">
                <a href="https://github.com/niazty" target="_blank" class="underline transition hover:text-black">GitHub</a>
                <a href="https://www.linkedin.com/in/muhammad-zakky-pusponegoro-ab6579287/" target="_blank" class="underline transition hover:text-black">LinkedIn</a>
            </div>
        </div>
  </footer>
</template>