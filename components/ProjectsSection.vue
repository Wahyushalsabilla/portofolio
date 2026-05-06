<template>
  <section id="projects" class="py-28 lg:py-36 bg-ink text-white relative overflow-hidden">
    <!-- Subtle dot pattern -->
    <div
      class="absolute inset-0 pointer-events-none opacity-10"
      style="background-image: radial-gradient(circle, rgba(255,255,255,0.3) 1px, transparent 1px); background-size: 32px 32px;"
      aria-hidden="true"
    />

    <div class="relative max-w-7xl mx-auto px-6 lg:px-12">
      <!-- Section label -->
      <div class="flex items-center gap-4 mb-16 reveal">
        <span class="text-xs font-sans font-medium tracking-[0.2em] uppercase text-mist">
          04 — Projects
        </span>
        <div class="flex-1 h-px bg-iron" />
      </div>

      <div class="flex flex-col lg:flex-row justify-between items-start gap-8 mb-16">
        <h2 class="font-display text-5xl lg:text-6xl font-light leading-tight text-white reveal">
          Selected<br /><em>Work</em>
        </h2>
        <p class="font-sans text-sm text-mist leading-relaxed max-w-sm self-end reveal reveal-delay-1">
          A selection of projects that reflect my passion for clean design and functional development.
        </p>
      </div>

      <!-- Projects grid -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-5">
        <div
          v-for="(project, index) in projects"
          :key="project.title"
          class="reveal group cursor-default"
          :class="[`reveal-delay-${Math.min(index + 1, 5)}`, index === 0 ? 'md:col-span-2' : '']"
        >
          <div class="h-full border border-iron rounded-3xl overflow-hidden hover:border-smoke transition-all duration-500 hover:-translate-y-1 hover:shadow-2xl hover:shadow-black/30 flex flex-col">
            
            <!-- Project image -->
            <div
              class="relative overflow-hidden bg-iron"
              :class="index === 0 ? 'h-52 lg:h-64' : 'h-40'"
            >
              <img
                v-if="project.images?.length"
                :src="project.images[activeImage % project.images.length]"
                :alt="project.title"
                class="w-full h-full object-cover transition-all duration-700 group-hover:scale-105"
              />

              <!-- Fallback kalau project belum punya gambar -->
              <div
                v-else
                class="w-full h-full bg-gradient-to-br from-iron via-[#242424] to-ink"
              />

              <!-- Elegant dark overlay -->
              <div class="absolute inset-0 bg-gradient-to-t from-black/75 via-black/20 to-transparent"></div>

              <!-- Category label -->
              <div class="absolute inset-0 flex items-end p-5">
                <span class="text-xs font-sans font-medium text-white/70 uppercase tracking-widest">
                  {{ project.category }}
                </span>
              </div>

              <!-- Hover overlay -->
              <div class="absolute inset-0 bg-white/5 opacity-0 group-hover:opacity-100 transition-opacity duration-300" />
            </div>

            <!-- Content -->
            <div class="p-6 flex flex-col flex-1">
              <h3 class="font-display text-2xl font-medium text-white mb-2">
                {{ project.title }}
              </h3>

              <p class="font-sans text-sm text-mist leading-relaxed mb-5 flex-1">
                {{ project.description }}
              </p>

              <!-- Tech tags -->
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="tech in project.tech"
                  :key="tech"
                  class="text-xs font-sans px-2.5 py-1 rounded-full border border-iron text-smoke group-hover:border-smoke transition-colors duration-300"
                >
                  {{ tech }}
                </span>
              </div>
            </div>

          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

import eduGrow1 from '@/assets/projects/edugrow/verification.png'
import eduGrow2 from '@/assets/projects/edugrow/classes.png'
import eduGrow3 from '@/assets/projects/edugrow/parent.png'
import eduGrow4 from '@/assets/projects/edugrow/growth.png'
import eduGrow5 from '@/assets/projects/edugrow/growth2.png'
import eduGrow6 from '@/assets/projects/edugrow/activity.png'

import elevacourse1 from '@/assets/projects/elevacourse/Sign-Up.png'
import elevacourse2 from '@/assets/projects/elevacourse/Dashboard.png'
import elevacourse3 from '@/assets/projects/elevacourse/Courses.png'

import timeToCode1 from '@/assets/projects/time-to-code/time-to-code.png'
import timeToCode2 from '@/assets/projects/time-to-code/qr-code.png'

import katalis1 from '@/assets/projects/katalis/aloevera.png'
import katalis2 from '@/assets/projects/katalis/calcium.png'
import katalis3 from '@/assets/projects/katalis/tips.png'
import katalis4 from '@/assets/projects/katalis/peppermint.png'

import misDynamic from '@/assets/projects/mis-dynamic/mis-dynamic.png'

const activeImage = ref(0)
let sliderInterval = null

onMounted(() => {
  sliderInterval = setInterval(() => {
    activeImage.value++
  }, 3500)
})

onBeforeUnmount(() => {
  clearInterval(sliderInterval)
})

const projects = [
  {
    title: 'TimeToCode',
    category: 'Educational Game · Gamified Learning',
    description:
      'An interactive programming learning game that combines branching storytelling, coding challenges, and strategic minigames to make computer science concepts more engaging for beginners. Players learn through narrative-driven gameplay, logic puzzles, code simulations, and multiplayer logic gate battles.',
    tech: ['Flutter','Dart', 'JavaScript', 'Gamification'],
    images: [timeToCode1, timeToCode2],
  },
  {
    title: 'EduGrow',
    category: 'Monitoring System · Web Platform',
    description:
      'A multi-role web platform for monitoring early childhood development, including student management, growth tracking, scheduling, and activity documentation.',
    tech: ['Nuxt', 'Laravel', 'MySQL', 'REST API', 'Tailwind CSS'],
    images: [eduGrow1, eduGrow2, eduGrow3, eduGrow4, eduGrow5, eduGrow6],
  },
  {
    title: 'Elevacourse',
    category: 'AI Platform',
    description:
      'An AI-powered learning platform built for Elevated Indonesia. It features a clean dashboard experience, intuitive course flow, and adaptive learning-oriented interface.',
    tech: ['Vue.js', 'Next', 'AI Integration', 'REST API'],
    images: [elevacourse1, elevacourse2, elevacourse3],
  },
  {
    title: 'Attendance App UI',
    category: 'Mobile · UI Design',
    description:
      'A mobile-first attendance tracking application UI focused on simplicity, clarity, and fast check-in interactions for users.',
    tech: ['Figma', 'UI/UX', 'Mobile Design', 'Prototyping'],
    images: [misDynamic],
  },
  {
    title: 'Katalis Carousel Design',
    category: 'Graphic Design',
    description:
      'A series of visually consistent social media carousel designs for Katalis Indonesia, crafted with clean typography, structured layouts, and brand-aligned visuals.',
    tech: ['Canva', 'Figma', 'Brand Design', 'Visual Content'],
    images: [katalis1, katalis2, katalis3, katalis4],
  },
]
</script>