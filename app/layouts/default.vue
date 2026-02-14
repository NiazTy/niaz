<script lang="ts" setup>
const open = ref(false);

const menus = [
    { name: "Home", to: "/" },
    { name: "About", to: "/about-me" },
    { name: "Portofolio", to: "/portofolio" },
    { name: "Blog", to: "/blog" },
];
</script>

<template>
    <header class="fixed top-0 left-0 w-full z-50 bg-[#f8f6ee]/80 backdrop-blur-md border-b border-gray-200">
        <nav class="max-w-7xl mx-auto px-6 md:px-12 h-20 flex items-center justify-between">
            <a href="/" class="font-snpro text-lg tracking-widest">PLACE FOR NIAZ</a>
            <ul class="hidden md:flex gap-10 font-snpro font-bold text-gray-700">
                <li v-for="menu in menus" :key="menu.name">
                    <a :href="menu.to" class="relative group">
                        {{ menu.name }}
                        <span class="absolute left-0 -bottom-1 w-0 h-0.5 bg-[#1a1b27] transition-all duration-300 group-hover:w-full" />
                    </a>
                </li>
            </ul>
            <button class="md:hidden" @click="open = !open">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-7 h-7" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                </svg>
            </button>
        </nav>
        <transition name="slide">
            <div v-if="open" class="md:hidden bg-[#f8f6ee] border-t border-gray-200">
                <ul class="flex flex-col items-center py-6 gap-6 font-medium">
                    <li v-for="menu in menus" :key="menu.name">
                        <a :href="menu.to" @click="open=false">{{ menu.name }}</a>
                    </li>
                </ul>
            </div>
        </transition>
    </header>
    <slot />
    <footer class="bg-[#1a1b27] text-white">
        <div class="max-w-7xl mx-auto px-6 py-12 text-center space-y-6">
            <h2 class="text-xl font-bold tracking-widest">
                Muhammad Zakky Pusponegoro
            </h2>
            <div class="flex justify-center gap-8 text-sm">
                <a href="https://instagram.com/m.niazyk" target="_blank" class="hover:text-gray-300">Instagram</a>
                <a href="https://www.linkedin.com/in/muhammad-zakky-pusponegoro-ab6579287/" target="_blank" class="hover:text-gray-300">LinkedIn</a>
                <a href="https://github.com/NiazTy" target="_blank" class="hover:text-gray-300">GitHub</a>
                <a href="mailto:hi@niaz.my.id" class="hover:text-gray-300">Email</a>
            </div>
            <p class="text-xs text-gray-400">
                © {{ new Date().getFullYear() }} All rights reserved.
            </p>
        </div>
    </footer>
</template>