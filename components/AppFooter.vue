<template>
  <footer class="bg-ink text-white py-12 px-6 lg:px-12">
    <div class="max-w-7xl mx-auto">
      <div class="flex flex-col lg:flex-row items-start lg:items-center justify-between gap-8">
        <!-- Left -->
        <div>
          <a href="#hero" class="font-display text-2xl font-light text-white mb-2 block">
            Shalsabilla <em>Wahyu</em>
          </a>
          <p class="font-sans text-xs text-smoke">Frontend Developer · UI/UX Designer · Graphic Designer</p>
          <p class="font-sans text-xs text-iron mt-1">Surabaya, Indonesia</p>
        </div>

        <!-- Center nav -->
        <nav class="flex flex-wrap gap-x-8 gap-y-2">
          <a
            v-for="item in footerLinks"
            :key="item.href"
            :href="item.href"
            class="text-xs font-sans text-smoke hover:text-white transition-colors duration-200"
          >
            {{ item.label }}
          </a>
        </nav>

        <!-- Right: socials -->
        <div class="flex items-center gap-3">
          <a
            href="https://www.linkedin.com/in/shalsabilla-wahyu-5304692a9/"
            target="_blank"
            rel="noopener"
            class="w-9 h-9 rounded-full border border-iron flex items-center justify-center hover:border-smoke transition-colors duration-200"
            aria-label="LinkedIn"
          >
            <svg class="w-4 h-4 text-smoke" fill="currentColor" viewBox="0 0 24 24">
              <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
            </svg>
          </a>
          <a
            href="mailto:shalsabillawahyuar@gmail.com"
            class="w-9 h-9 rounded-full border border-iron flex items-center justify-center hover:border-smoke transition-colors duration-200"
            aria-label="Email"
          >
            <svg class="w-4 h-4 text-smoke" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
          </a>
        </div>
      </div>

      <div class="h-px bg-iron my-8" />

      <div class="flex flex-col sm:flex-row items-center justify-between gap-4">
        <p class="text-xs font-sans text-iron">
          © {{ new Date().getFullYear() }} Shalsabilla Wahyu. Crafted with intention.
        </p>
        <p class="text-xs font-sans text-iron">
          Built with Nuxt 3 + Tailwind CSS
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup>
const footerLinks = [
  { label: 'About', href: '#about' },
  { label: 'Experience', href: '#experience' },
  { label: 'Skills', href: '#skills' },
  { label: 'Projects', href: '#projects' },
  { label: 'Gallery', href: '#gallery' },
  { label: 'Contact', href: '#contact' },
]
</script>
