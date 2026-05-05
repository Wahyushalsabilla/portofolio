<!-- <template>
  <section id="gallery" class="py-28 lg:py-36 bg-snow relative overflow-hidden">
    <div class="max-w-7xl mx-auto px-6 lg:px-12">
      <div class="section-rule reveal">
        <span class="text-xs font-sans font-medium tracking-[0.2em] uppercase text-smoke">05 — Gallery</span>
      </div>

      <div class="flex flex-col lg:flex-row justify-between items-end mb-12 gap-6">
        <h2 class="font-display text-5xl lg:text-6xl font-light leading-tight text-ink reveal">
          Design<br /><em>Moments</em>
        </h2>

        <div class="flex items-center gap-3 reveal reveal-delay-1">
          <button
            @click="prev"
            class="w-12 h-12 rounded-full border border-silver flex items-center justify-center hover:border-ink hover:bg-ink hover:text-white transition-all duration-300 group"
            aria-label="Previous slide"
          >
            <svg class="w-5 h-5 text-smoke group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 19l-7-7 7-7" />
            </svg>
          </button>
          <span class="font-display text-sm text-smoke">
            {{ String(current + 1).padStart(2, '0') }} / {{ String(slides.length).padStart(2, '0') }}
          </span>
          <button
            @click="next"
            class="w-12 h-12 rounded-full border border-silver flex items-center justify-center hover:border-ink hover:bg-ink hover:text-white transition-all duration-300 group"
            aria-label="Next slide"
          >
            <svg class="w-5 h-5 text-smoke group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 5l7 7-7 7" />
            </svg>
          </button>
        </div>
      </div>

      <div
        class="relative overflow-hidden rounded-3xl reveal reveal-delay-1"
        ref="track"
        @touchstart="onTouchStart"
        @touchmove="onTouchMove"
        @touchend="onTouchEnd"
      >
        <div
          class="flex transition-transform duration-700 ease-[cubic-bezier(0.16,1,0.3,1)]"
          :style="{ transform: `translateX(-${current * 100}%)` }"
        >
          <div
            v-for="(slide, i) in slides"
            :key="i"
            class="min-w-full"
          >
            <div
              class="relative h-80 lg:h-[500px] rounded-3xl overflow-hidden border border-pearl shadow-2xl shadow-ink/10"
              :style="{ background: slide.bg }"
            >

              <div class="absolute inset-0 flex flex-col items-center justify-center gap-4">
                <div
                  class="w-20 h-20 rounded-2xl border border-white/20 flex items-center justify-center"
                  style="background: rgba(255,255,255,0.1); backdrop-filter: blur(8px);"
                >
                  <component
                    :is="slide.icon"
                    class="w-8 h-8 text-white"
                  />
                </div>
                <div class="text-center">
                  <p class="font-display text-2xl font-light text-white">{{ slide.title }}</p>
                  <p class="font-sans text-sm text-white/60 mt-1">{{ slide.subtitle }}</p>
                </div>
                <p class="text-xs font-sans text-white/40 mt-2">Replace with your actual screenshot</p>
              </div>

              <div class="absolute bottom-0 left-0 right-0 p-8" style="background: linear-gradient(transparent, rgba(0,0,0,0.4));">
                <span class="text-xs font-sans text-white/50 uppercase tracking-widest">{{ slide.tag }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="flex items-center justify-center gap-2 mt-6 reveal reveal-delay-2">
        <button
          v-for="(_, i) in slides"
          :key="i"
          @click="goTo(i)"
          class="transition-all duration-300 rounded-full"
          :class="i === current ? 'w-8 h-2 bg-ink' : 'w-2 h-2 bg-silver hover:bg-smoke'"
          :aria-label="`Go to slide ${i + 1}`"
        />
      </div>

      <div class="flex gap-3 mt-8 overflow-x-auto pb-2 reveal reveal-delay-2 scrollbar-none">
        <button
          v-for="(slide, i) in slides"
          :key="i"
          @click="goTo(i)"
          class="shrink-0 w-20 h-14 rounded-xl overflow-hidden border-2 transition-all duration-300"
          :class="i === current ? 'border-ink shadow-lg' : 'border-transparent opacity-50 hover:opacity-80'"
          :style="{ background: slide.bg }"
          :aria-label="`Thumbnail ${i + 1}`"
        >
        <div class="w-full h-full flex items-center justify-center">
          <component
            :is="slide.icon"
            class="w-5 h-5 text-white/70"
          />
        </div>
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import {
  Gamepad2,
  GraduationCap,
  Smartphone,
  BookOpen,
  Sparkles
} from 'lucide-vue-next'
const current = ref(0)
const track = ref(null)
let touchStartX = 0
let touchDeltaX = 0

const slides = [
  {
    title: 'TimeToCode',
    subtitle: 'Story-based coding game',
    icon: Gamepad2,
    tag: 'Web App',
    bg: 'linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%)',
  },
  {
    title: 'Elevacourse UI',
    subtitle: 'AI Learning Platform',
    icon: GraduationCap,
    tag: 'Platform Design',
    bg: 'linear-gradient(135deg, #202020 0%, #383838 100%)',
  },
  {
    title: 'Attendance App',
    subtitle: 'Mobile UI Design',
    icon: Smartphone,
    tag: 'Mobile Design',
    bg: 'linear-gradient(135deg, #181818 0%, #303030 100%)',
  },
  {
    title: 'EduGrow',
    subtitle: 'Learning Platform',
    icon: BookOpen,
    tag: 'Full Stack',
    bg: 'linear-gradient(135deg, #1c1c1c 0%, #343434 100%)',
  },
  {
    title: 'Katalis Carousel',
    subtitle: 'Social Media Design',
    icon: Sparkles,
    tag: 'Graphic Design',
    bg: 'linear-gradient(135deg, #222 0%, #3c3c3c 100%)',
  },
]

const next = () => {
  current.value = (current.value + 1) % slides.length
}

const prev = () => {
  current.value = (current.value - 1 + slides.length) % slides.length
}

const goTo = (i) => {
  current.value = i
}

// Touch/swipe support
const onTouchStart = (e) => {
  touchStartX = e.touches[0].clientX
}

const onTouchMove = (e) => {
  touchDeltaX = e.touches[0].clientX - touchStartX
}

const onTouchEnd = () => {
  if (touchDeltaX < -50) next()
  else if (touchDeltaX > 50) prev()
  touchDeltaX = 0
}

// Auto-advance
let autoPlay = null
onMounted(() => {
  autoPlay = setInterval(next, 5000)
})

onUnmounted(() => {
  if (autoPlay) clearInterval(autoPlay)
})
</script>

<style scoped>
.scrollbar-none::-webkit-scrollbar {
  display: none;
}
.scrollbar-none {
  scrollbar-width: none;
}
</style> -->
