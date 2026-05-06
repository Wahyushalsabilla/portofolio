<template>
  <section id="skills" class="py-28 lg:py-36 bg-white relative overflow-hidden">
    <div class="max-w-7xl mx-auto px-6 lg:px-12">
      <!-- Section label -->
      <div class="section-rule reveal">
        <span class="text-xs font-sans font-medium tracking-[0.2em] uppercase text-smoke">03 — Tech Stack</span>
      </div>

      <div class="flex flex-col lg:flex-row gap-12 lg:gap-20 mb-16">
        <h2 class="font-display text-5xl lg:text-6xl font-light leading-tight text-ink reveal whitespace-nowrap">
          Skills &<br /><em>Expertise</em>
        </h2>
        <p class="font-sans text-base text-smoke leading-relaxed max-w-lg self-end reveal reveal-delay-1">
          A versatile toolkit spanning design and development — enabling me to take ideas from concept to polished, production-ready products.
        </p>
      </div>

      <!-- Skill Categories -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-5">
        <div
          v-for="(category, ci) in skillCategories"
          :key="category.name"
          class="reveal group"
          :class="`reveal-delay-${Math.min(ci + 1, 5)}`"
        >
          <div
            class="h-full border border-pearl rounded-3xl p-6 lg:p-7 hover:border-ink/20 hover:shadow-xl hover:shadow-ink/5 transition-all duration-500 hover:-translate-y-1"
          >
            <!-- Category header -->
            <div class="flex items-center gap-3 mb-6">
              <div class="w-8 h-8 rounded-xl bg-ink flex items-center justify-center shrink-0">
                <component
              :is="category.icon"
              class="w-4 h-4 text-white"
            />
              </div>
              <h3 class="font-sans text-sm font-semibold text-ink uppercase tracking-wider">{{ category.name }}</h3>
            </div>

            <!-- Skills list -->
           <ul class="space-y-5">
            <li
              v-for="skill in category.skills"
              :key="skill.name"
              class="group/skill pl-4 border-l border-pearl/60 hover:border-ink/30 hover:pl-5 transition-all duration-300"
            >
              <p class="text-sm font-medium text-ink font-sans leading-tight">
                {{ skill.name }}
              </p>
              <p class="text-xs text-smoke font-sans mt-1 leading-snug">
                {{ skill.desc }}
              </p>
            </li>
          </ul>
          </div>
        </div>
      </div>

      <!-- Additional tools strip -->
      <div class="mt-10 p-6 rounded-3xl border border-pearl bg-snow reveal reveal-delay-3">
        <p class="text-xs font-sans text-mist uppercase tracking-widest mb-4">Also familiar with</p>
        <div class="flex flex-wrap gap-2">
          <span
            v-for="tool in additionalTools"
            :key="tool"
            class="px-3 py-1.5 text-xs font-sans font-medium text-smoke border border-silver rounded-full hover:border-ink hover:text-ink transition-colors duration-200 bg-white"
          >
            {{ tool }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import {
  Code2,
  PenTool,
  Server,
  Check,
} from 'lucide-vue-next'
const skillCategories = [
  {
    name: 'Frontend',
    icon: Code2,
    skills: [
      { name: 'Vue / Nuxt', desc: 'Building responsive and dynamic web interfaces' },
      { name: 'Tailwind CSS', desc: 'Creating modern layouts and UI consistency' },
      { name: 'TypeScript', desc: 'Writing scalable and maintainable code' },
      { name: 'HTML / CSS', desc: 'Semantic markup and pixel-perfect styling' },
    ],
  },
  {
    name: 'Design',
    icon: PenTool,
    skills: [
      { name: 'Figma', desc: 'UI design, wireframing, and prototyping' },
      { name: 'Canva', desc: 'Social media and visual content design' },
      { name: 'UI/UX Design', desc: 'User flow, research, and interface optimization' },
      { name: 'Graphic Design', desc: 'Brand identity and visual communication' },
    ],
  },
  {
    name: 'Backend & Tools',
    icon: Server,
    skills: [
      { name: 'PHP / Laravel', desc: 'Backend logic and RESTful API development' },
      { name: 'MySQL / MongoDB', desc: 'Relational and document-based data management' },
      { name: 'Git / GitHub', desc: 'Version control and collaborative workflows' },
      { name: 'REST API', desc: 'API integration and consumption' },
    ],
  },
]

const additionalTools = [
  'React', 'GitLab', 'Postman', 'Bootstrap',
  'SCSS', 'Vite', 'VS Code', 'Notion', 'Canva', 'PicsArt', 
  'CapCut'
]
</script>
