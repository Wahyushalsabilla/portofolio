<template>
  <section id="experience" class="py-28 lg:py-36 bg-snow relative overflow-hidden">
    <!-- Background texture -->
    <div
      class="absolute inset-0 pointer-events-none opacity-30"
      style="background-image: radial-gradient(circle at 80% 20%, rgba(168,168,168,0.15) 0%, transparent 50%);"
      aria-hidden="true"
    />

    <div class="max-w-7xl mx-auto px-6 lg:px-12">
      <!-- Section label -->
      <div class="section-rule reveal">
        <span class="text-xs font-sans font-medium tracking-[0.2em] uppercase text-smoke">02 — Experience</span>
      </div>

      <div class="max-w-4xl">
        <h2 class="font-display text-5xl lg:text-6xl font-light leading-tight text-ink mb-16 reveal">
          Where I've<br /><em>grown</em> professionally.
        </h2>
      </div>

      <!-- Timeline -->
      <div class="relative">
        <!-- Vertical line -->
        <div class="absolute left-4 lg:left-8 top-0 bottom-0 w-px bg-silver hidden sm:block" aria-hidden="true" />

        <div class="space-y-8">
          <div
            v-for="(exp, index) in experiences"
            :key="exp.role"
            class="relative pl-0 sm:pl-20 reveal"
            :class="`reveal-delay-${Math.min(index + 1, 5)}`"
          >
            <!-- Timeline dot -->
            <div
              class="absolute left-0 lg:left-4 top-6 w-8 h-8 rounded-full border-2 border-silver bg-white flex items-center justify-center hidden sm:flex z-10 -translate-x-4 lg:-translate-x-4"
              :style="{ borderColor: index === 0 ? '#0a0a0a' : undefined, background: index === 0 ? '#0a0a0a' : undefined }"
            >
              <span class="text-xs font-sans font-medium" :class="index === 0 ? 'text-white' : 'text-smoke'">
                {{ String(experiences.length - index).padStart(2, '0') }}
              </span>
            </div>

            <!-- Card -->
            <div
              class="group glass-card rounded-3xl p-6 lg:p-8 hover:shadow-xl hover:shadow-ink/8 transition-all duration-500 hover:-translate-y-1 cursor-default border border-pearl/60"
            >
              <div class="flex flex-col lg:flex-row lg:items-start justify-between gap-4 mb-4">
                <div>
                  <div class="flex items-center gap-2 mb-1">
                    <span
                      v-if="index === 0"
                      class="text-[10px] font-sans font-medium px-2 py-0.5 bg-ink text-white rounded-full uppercase tracking-wider"
                    >
                      Recent
                    </span>
                    <span class="text-xs font-sans text-mist uppercase tracking-widest">{{ exp.type }}</span>
                  </div>
                  <h3 class="font-display text-2xl lg:text-3xl font-medium text-ink leading-tight">{{ exp.role }}</h3>
                  <p class="font-sans text-sm text-smoke mt-1">{{ exp.company }}</p>
                </div>

                <div class="shrink-0">
                  <span class="inline-flex items-center gap-1.5 px-4 py-2 rounded-full border border-pearl text-xs font-sans text-smoke bg-white/60">
                    <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
                    </svg>
                    {{ exp.period }}
                  </span>
                </div>
              </div>

              <!-- Description -->
              <p class="font-sans text-sm text-smoke leading-relaxed mb-5">{{ exp.description }}</p>

              <!-- Tags -->
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="tag in exp.tags"
                  :key="tag"
                  class="text-xs font-sans px-3 py-1 rounded-full border border-pearl text-smoke bg-white/80 group-hover:border-silver transition-colors duration-300"
                >
                  {{ tag }}
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
const experiences = [
  {
    role: 'Front-End Developer',
    company: 'PT Oxioo Teknologi Indonesia',
    period: 'Jan 2026 — Present',
    type: 'Internship',
    description:
      'Developed responsive web applications using Nuxt.js (Vue). Implemented key features such as dashboards, learning progress tracking, and user authentication. Integrated REST APIs and handled state management (loading, error) to ensure a smooth user experience. Collaborated in an agile team using Git and sprint-based workflows.',
    tags: ['Vue.js', 'Nuxt.js', 'Tailwind CSS', 'REST API', 'Git'],
  },
  {
    role: 'Front-End Developer / Manager',
    company: 'Elevated Indonesia',
    period: 'Aug 2025 — Dec 2025',
    type: 'Internship',
    description:
      'Led and contributed to frontend development of the Elevacourse AI learning platform. Managed team tasks, conducted code reviews, and ensured UI consistency. Collaborated with cross-functional teams to align design and system performance.',
    tags: ['Vue.js', 'Leadership', 'Project Management', 'UI Development'],
  },
  {
    role: 'Graphic Designer',
    company: 'Katalis Indonesia',
    period: 'Aug 2025 — Present',
    type: 'Professional',
    description:
      'Designed educational and storytelling-based visual content for social media. Created Instagram carousel designs aligned with brand guidelines and improved audience engagement through visually compelling content.',
    tags: ['Canva', 'Figma', 'Brand Design', 'Social Media'],
  },
  {
    role: 'UI/UX Designer',
    company: 'ECODE HIMIT',
    period: 'Jan 2024 — Present',
    type: 'Organization',
    description:
      'Redesigned attendance system UI/UX to improve usability and accessibility. Developed scalable design components and improved the experience for over 300+ new students.',
    tags: ['Figma', 'Wireframing', 'Prototyping', 'User Research'],
  },
  {
    role: 'Liaison Officer',
    company: 'PKKMB PENS 2024',
    period: 'Jul 2024 — Aug 2024',
    type: 'Event',
    description:
      'Acted as a communication bridge between committees and participants during campus orientation. Ensured smooth coordination, guided new students, and minimized miscommunication throughout the event.',
    tags: ['Communication', 'Coordination', 'Event Management'],
  },
]
</script>
