<template>
  <section
    id="hero"
    class="relative min-h-screen flex flex-col justify-center overflow-hidden bg-white"
  >
    <!-- Subtle grid background -->
    <div class="absolute inset-0 pointer-events-none" aria-hidden="true">
      <div
        class="absolute inset-0"
        style="background-image: linear-gradient(rgba(168,168,168,0.08) 1px, transparent 1px), linear-gradient(90deg, rgba(168,168,168,0.08) 1px, transparent 1px); background-size: 72px 72px;"
      />
    </div>

    <!-- Floating accent circle -->
    <div
      class="absolute right-0 top-1/2 -translate-y-1/2 w-[500px] h-[500px] rounded-full pointer-events-none"
      style="background: radial-gradient(circle, rgba(200,200,200,0.15) 0%, transparent 70%); transform: translate(30%, -50%);"
      aria-hidden="true"
    />

    <div class="relative max-w-7xl mx-auto px-6 lg:px-12 pt-28 pb-16">
      <div class="grid lg:grid-cols-2 gap-16 items-center">
        <!-- Left: Text -->
        <div>
          <!-- Status badge -->
          <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full border border-silver bg-snow text-xs font-medium text-smoke mb-10 animate-fade-in">
            <span class="w-2 h-2 rounded-full bg-ink animate-pulse inline-block" />
            Available for opportunities
          </div>

          <!-- Name -->
          <h1
            class="font-display text-6xl lg:text-8xl font-light leading-[1.02] tracking-tight text-ink mb-4 animate-fade-up"
            style="animation-delay: 0.1s; animation-fill-mode: both;"
          >
            Shalsabilla<br />
            <span class="italic font-light">Wahyu</span>
          </h1>

          <!-- Role pills -->
          <div
            class="flex flex-wrap gap-2 mb-8 animate-fade-up"
            style="animation-delay: 0.2s; animation-fill-mode: both;"
          >
            <span
              v-for="role in roles"
              :key="role"
              class="px-3 py-1 text-xs font-medium border border-silver rounded-full text-smoke hover:border-ink hover:text-ink transition-colors duration-200"
            >
              {{ role }}
            </span>
          </div>

          <!-- Tagline -->
          <p
            class="font-sans text-base text-smoke leading-relaxed max-w-md mb-10 animate-fade-up"
            style="animation-delay: 0.3s; animation-fill-mode: both;"
          >
            Informatics Engineering student crafting beautiful interfaces and meaningful experiences — where design meets code.
          </p>

          <!-- CTAs -->
          <div
            class="flex flex-wrap gap-4 animate-fade-up"
            style="animation-delay: 0.4s; animation-fill-mode: both;"
          >
            <a
              href="#projects"
              class="inline-flex items-center gap-2 px-7 py-3.5 bg-ink text-white text-sm font-medium rounded-full hover:bg-iron transition-all duration-300 hover:shadow-xl hover:shadow-ink/15 hover:-translate-y-0.5 group"
            >
              View Work
              <svg class="w-4 h-4 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3" />
              </svg>
            </a>
            <a
              href="#contact"
              class="inline-flex items-center gap-2 px-7 py-3.5 border border-silver text-ink text-sm font-medium rounded-full hover:border-ink transition-all duration-300 hover:-translate-y-0.5"
            >
              Get in Touch
            </a>
          </div>

          <!-- Social links -->
          <div
            class="flex items-center gap-4 mt-10 animate-fade-up"
            style="animation-delay: 0.5s; animation-fill-mode: both;"
          >
            <a
              href="https://www.linkedin.com/in/shalsabilla-wahyu-5304692a9/"
              target="_blank"
              rel="noopener"
              class="flex items-center gap-2 text-xs text-smoke hover:text-ink transition-colors group"
            >
              <span class="font-medium group-hover:underline">LinkedIn</span>
              <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" />
              </svg>
            </a>
            <span class="text-silver">·</span>
            <span class="text-xs text-mist">Surabaya, Indonesia</span>
          </div>
        </div>

        <!-- Right: Portrait card -->
        <div
          class="flex justify-center lg:justify-end animate-fade-up"
          style="animation-delay: 0.2s; animation-fill-mode: both;"
        >
          <div class="relative">
            <!-- Main portrait frame -->
            <div
              class="w-72 h-96 lg:w-80 lg:h-[26rem] rounded-3xl overflow-hidden border border-pearl shadow-2xl shadow-ink/10 relative"
              style="background: linear-gradient(145deg, #f0f0f0 0%, #e0e0e0 100%);"
            >
              <!-- Placeholder portrait with initials -->
              <img
                :src="myPhoto"
                alt="Shalsabilla"
                class="w-full h-full object-cover"
              />

              <!-- Overlay gradient -->
              <div class="absolute inset-x-0 bottom-0 h-1/3" style="background: linear-gradient(transparent, rgba(232,232,232,0.6));" />
            </div>

            <!-- Floating stat cards -->
            <div
              class="absolute -left-8 top-10 glass-card rounded-2xl px-4 py-3 shadow-lg"
            >
              <p class="text-xs text-smoke font-sans">Projects</p>
              <p class="font-display text-2xl font-medium text-ink">5+</p>
            </div>

            <div
              class="absolute -right-6 bottom-14 glass-card rounded-2xl px-4 py-3 shadow-lg"
            >
              <p class="text-xs text-smoke font-sans">Experience</p>
              <p class="font-display text-2xl font-medium text-ink">5 Roles</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll indicator -->
    <div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 animate-fade-in" style="animation-delay: 1s; animation-fill-mode: both;">
      <span class="text-xs text-mist font-sans tracking-widest uppercase">Scroll</span>
      <div class="w-px h-10 bg-gradient-to-b from-silver to-transparent" />
    </div>

    <!-- Marquee strip -->
    <div class="absolute bottom-0 left-0 right-0 border-t border-pearl overflow-hidden py-3 bg-snow/60">
      <div class="flex">
        <div class="marquee-track">
          <span v-for="tag in [...tags, ...tags]" :key="tag + Math.random()" class="text-xs text-mist font-sans tracking-widest uppercase shrink-0">
            {{ tag }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import myPhoto from '../assets/my-photo/Shalsabilla.png'
const roles = ['Frontend Developer', 'UI/UX Designer', 'Graphic Designer']

const tags = [
  'Vue · Nuxt ·',
  'Tailwind CSS ·',
  'Figma ·',
  'UI/UX Design ·',
  'Graphic Design ·',
  'TypeScript ·',
  'Laravel ·',
  'Canva ·',
  'React ·',
  'MySQL ·',
]
</script>
