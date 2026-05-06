<template>
  <section id="about" class="py-28 lg:py-36 bg-white relative overflow-hidden">
    <!-- Decorative line -->
    <div class="absolute left-0 top-0 bottom-0 w-px bg-gradient-to-b from-transparent via-silver to-transparent hidden lg:block" />

    <div class="max-w-7xl mx-auto px-6 lg:px-12">
      <!-- Section label -->
      <div class="section-rule reveal">
        <span class="text-xs font-sans font-medium tracking-[0.2em] uppercase text-smoke">01 — About</span>
      </div>

      <div class="grid lg:grid-cols-2 gap-16 lg:gap-24 items-start">
        <!-- Left -->
        <div>
          <h2 class="font-display text-5xl lg:text-6xl font-light leading-tight text-ink mb-8 reveal">
            Crafting digital<br />
            <em>experiences</em> with<br />
            intention.
          </h2>

          <p class="font-sans text-base text-smoke leading-relaxed mb-6 reveal reveal-delay-1">
            I am an Informatics Engineering student with a deep passion for the intersection of visual design and frontend development. I believe that great digital products are born when aesthetics and functionality work in perfect harmony.
          </p>

          <p class="font-sans text-base text-smoke leading-relaxed mb-10 reveal reveal-delay-2">
            With experience spanning UI/UX design, graphic design, and frontend engineering, I bring a holistic perspective to every project — from initial wireframes to production-ready interfaces.
          </p>

          <!-- Values / traits -->
          <div class="grid grid-cols-2 gap-4 reveal reveal-delay-3">
            <div
              v-for="trait in traits"
              :key="trait.label"
              class="p-4 rounded-2xl border border-pearl hover:border-silver transition-colors duration-300 group"
            >
              <component :is="trait.icon" class="w-5 h-5 text-mist mb-2" />
              <p class="text-sm font-medium text-ink">{{ trait.label }}</p>
              <p class="text-xs text-smoke mt-1">{{ trait.desc }}</p>
            </div>
          </div>
        </div>

        <!-- Right: Stats & Details -->
        <div class="reveal reveal-delay-2">
          <!-- Detail list -->
          <div class="space-y-0 border border-pearl rounded-3xl overflow-hidden">
            <div
              v-for="(detail, i) in details"
              :key="detail.label"
              class="flex items-start gap-4 p-5 hover:bg-snow transition-colors duration-200"
              :class="i < details.length - 1 ? 'border-b border-pearl' : ''"
            >
              <div class="w-8 h-8 rounded-full bg-snow border border-pearl flex items-center justify-center shrink-0 mt-0.5">
                <component :is="detail.icon" class="w-4 h-4 text-mist" />
              </div>
              <div>
                <p class="text-xs text-mist font-sans uppercase tracking-wider mb-0.5">{{ detail.label }}</p>
                <p class="text-sm font-medium text-ink font-sans">{{ detail.value }}</p>
              </div>
            </div>
          </div>

          <!-- Stat cards row -->
          <div class="grid grid-cols-3 gap-3 mt-4">
            <div
              v-for="stat in stats"
              :key="stat.label"
              class="text-center p-4 rounded-2xl bg-snow border border-pearl"
            >
              <p class="font-display text-3xl font-light text-ink">{{ stat.number }}</p>
              <p class="text-xs text-smoke font-sans mt-1">{{ stat.label }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import {
  Sparkles,
  User,
  Users,
  Zap,
  MapPin,
  GraduationCap,
  Mail,
  Linkedin,
  Briefcase
} from 'lucide-vue-next'
const traits = [
  { icon: Sparkles, label: 'Detail-oriented', desc: 'Pixel-perfect execution' },
  { icon: User, label: 'User-focused', desc: 'Empathy-driven design' },
  { icon: Users, label: 'Collaborative', desc: 'Strong team player' },
  { icon: Zap, label: 'Fast learner', desc: 'Adapts to new tools' },
]

const details = [
  { icon: MapPin, label: 'Location', value: 'Surabaya, Indonesia' },
  { icon: GraduationCap, label: 'Education', value: 'Informatics Engineering' },
  { icon: Mail, label: 'Email', value: 'shalsabillawahyuar@gmail.com' },
  { icon: Linkedin, label: 'LinkedIn', value: 'shalsabilla-wahyu-5304692a9' },
  { icon: Briefcase, label: 'Status', value: 'Open to opportunities' },
]

const stats = [
  { number: '5+', label: 'Projects' },
  { number: '3', label: 'Roles Held' },
  { number: '3+', label: 'Years Study' },
]
</script>
