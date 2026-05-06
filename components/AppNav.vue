<template>
  <header
    class="fixed top-0 left-0 right-0 z-50 transition-all duration-500"
    :class="scrolled ? 'py-3 glass-card shadow-sm' : 'py-6 bg-transparent'"
  >
    <div class="max-w-7xl mx-auto px-6 lg:px-12 flex items-center justify-between">
      <!-- Logo -->
      <a href="#hero" class="font-display text-xl font-medium tracking-tight text-ink">
        SW<span class="text-smoke">.</span>
      </a>

      <!-- Desktop Nav -->
      <nav class="hidden md:flex items-center gap-8">
        <a
          v-for="item in navItems"
          :key="item.href"
          :href="item.href"
          class="nav-link text-sm font-sans font-medium text-smoke hover:text-ink transition-colors duration-200"
        >
          {{ item.label }}
        </a>
      </nav>

      <!-- CTA -->
      <a
        href="mailto:shalsabillawahyuar@gmail.com"
        class="hidden md:inline-flex items-center gap-2 text-sm font-medium px-5 py-2.5 bg-ink text-white rounded-full hover:bg-iron transition-all duration-300 hover:shadow-lg hover:shadow-ink/10 hover:-translate-y-0.5"
      >
        Hire Me
      </a>

      <!-- Mobile Menu Toggle -->
      <button
        class="md:hidden flex flex-col gap-1.5 p-2"
        @click="menuOpen = !menuOpen"
        aria-label="Toggle menu"
      >
        <span
          class="block w-6 h-px bg-ink transition-all duration-300"
          :class="menuOpen ? 'rotate-45 translate-y-2' : ''"
        />
        <span
          class="block w-6 h-px bg-ink transition-all duration-300"
          :class="menuOpen ? 'opacity-0' : ''"
        />
        <span
          class="block w-6 h-px bg-ink transition-all duration-300"
          :class="menuOpen ? '-rotate-45 -translate-y-2' : ''"
        />
      </button>
    </div>

    <!-- Mobile Menu -->
    <Transition name="slide-down">
      <div
        v-if="menuOpen"
        class="md:hidden glass-card mt-2 mx-4 rounded-2xl p-6"
      >
        <nav class="flex flex-col gap-4">
          <a
            v-for="item in navItems"
            :key="item.href"
            :href="item.href"
            class="text-base font-medium text-smoke hover:text-ink transition-colors"
            @click="menuOpen = false"
          >
            {{ item.label }}
          </a>
          <a
            href="mailto:shalsabillawahyuar@gmail.com"
            class="inline-flex items-center justify-center text-sm font-medium px-5 py-2.5 bg-ink text-white rounded-full mt-2"
            @click="menuOpen = false"
          >
            Hire Me
          </a>
        </nav>
      </div>
    </Transition>
  </header>
</template>

<script setup> 
const scrolled = ref(false)
const menuOpen = ref(false)

const navItems = [
  { label: 'About', href: '#about' },
  { label: 'Experience', href: '#experience' },
  { label: 'Skills', href: '#skills' },
  { label: 'Projects', href: '#projects' },
  { label: 'Gallery', href: '#gallery' },
  { label: 'Contact', href: '#contact' },
]

onMounted(() => {
  window.addEventListener('scroll', () => {
    scrolled.value = window.scrollY > 40
  })
})
</script>

<style scoped>
.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.3s ease;
}
.slide-down-enter-from,
.slide-down-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
