<template>
  <section id="contact" class="py-28 lg:py-36 bg-white relative overflow-hidden">
    <!-- Background shape -->
    <div
      class="absolute right-0 bottom-0 w-96 h-96 pointer-events-none"
      style="background: radial-gradient(circle at 100% 100%, rgba(168,168,168,0.08) 0%, transparent 70%);"
      aria-hidden="true"
    />

    <div class="max-w-7xl mx-auto px-6 lg:px-12">
      <!-- Section label -->
      <div class="section-rule reveal">
        <span class="text-xs font-sans font-medium tracking-[0.2em] uppercase text-smoke">07 — Contact</span>
      </div>

      <div class="grid lg:grid-cols-2 gap-16 lg:gap-24 items-start">
        <!-- Left: CTA text -->
        <div>
          <h2 class="font-display text-5xl lg:text-7xl font-light leading-[1.05] text-ink mb-8 reveal">
            Let's create<br />something<br /><em>beautiful</em><br />together.
          </h2>

          <p class="font-sans text-base text-smoke leading-relaxed mb-10 max-w-md reveal reveal-delay-1">
            Whether you have a project in mind, need a designer, or just want to say hello — my inbox is always open.
          </p>

          <!-- Contact cards -->
          <div class="space-y-3 reveal reveal-delay-2">
            <a
              v-for="contact in contactLinks"
              :key="contact.label"
              :href="contact.href"
              :target="contact.external ? '_blank' : undefined"
              rel="noopener"
              class="flex items-center gap-4 p-4 rounded-2xl border border-pearl hover:border-ink transition-all duration-300 group hover:shadow-md hover:-translate-y-0.5"
            >
              <div class="w-10 h-10 rounded-xl bg-snow border border-pearl flex items-center justify-center shrink-0 group-hover:bg-ink group-hover:border-ink transition-all duration-300">
                <component
                  :is="contact.icon"
                  class="w-5 h-5 text-ink group-hover:text-white transition"
                />
              </div>
              <div>
                <p class="text-xs text-mist font-sans uppercase tracking-wider">{{ contact.label }}</p>
                <p class="text-sm font-medium text-ink group-hover:text-smoke transition-colors font-sans">{{ contact.value }}</p>
              </div>
              <svg class="w-4 h-4 text-silver ml-auto group-hover:text-ink group-hover:translate-x-1 transition-all duration-300" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3" />
              </svg>
            </a>
          </div>
        </div>

        <!-- Right: Form -->
        <div class="reveal reveal-delay-2">
          <div class="border border-pearl rounded-3xl p-8 lg:p-10">
            <h3 class="font-display text-2xl font-medium text-ink mb-6">Send a message</h3>

            <form @submit.prevent="handleSubmit" class="space-y-5">
              <div>
                <label class="block text-xs font-sans font-medium text-smoke uppercase tracking-wider mb-2">Your Name</label>
                <input
                  v-model="form.name"
                  type="text"
                  placeholder="Your Name"
                  required
                  class="w-full px-4 py-3.5 rounded-xl border border-pearl bg-snow font-sans text-sm text-ink placeholder-mist focus:outline-none focus:border-ink transition-colors duration-200"
                />
              </div>

              <div>
                <label class="block text-xs font-sans font-medium text-smoke uppercase tracking-wider mb-2">Email Address</label>
                <input
                  v-model="form.email"
                  type="email"
                  placeholder="youremail@example.com"
                  required
                  class="w-full px-4 py-3.5 rounded-xl border border-pearl bg-snow font-sans text-sm text-ink placeholder-mist focus:outline-none focus:border-ink transition-colors duration-200"
                />
              </div>

              <div>
                <label class="block text-xs font-sans font-medium text-smoke uppercase tracking-wider mb-2">Subject</label>
                <input
                  v-model="form.subject"
                  type="text"
                  placeholder="Project Collaboration"
                  class="w-full px-4 py-3.5 rounded-xl border border-pearl bg-snow font-sans text-sm text-ink placeholder-mist focus:outline-none focus:border-ink transition-colors duration-200"
                />
              </div>

              <div>
                <label class="block text-xs font-sans font-medium text-smoke uppercase tracking-wider mb-2">Message</label>
                <textarea
                  v-model="form.message"
                  rows="5"
                  placeholder="Tell me about your project..."
                  required
                  class="w-full px-4 py-3.5 rounded-xl border border-pearl bg-snow font-sans text-sm text-ink placeholder-mist focus:outline-none focus:border-ink transition-colors duration-200 resize-none"
                />
              </div>

              <button
                type="submit"
                class="w-full py-4 bg-ink text-white text-sm font-medium rounded-xl hover:bg-iron transition-all duration-300 hover:shadow-xl hover:shadow-ink/20 hover:-translate-y-0.5 flex items-center justify-center gap-2 group"
              >
                <span>{{ submitted ? 'Message Sent ✓' : 'Send Message' }}</span>
                <svg
                  v-if="!submitted"
                  class="w-4 h-4 group-hover:translate-x-1 transition-transform"
                  fill="none"
                  stroke="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M22 2L11 13M22 2l-7 20-4-9-9-4 20-7z" />
                </svg>
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Mail, Briefcase, MapPin } from 'lucide-vue-next'
import emailjs from '@emailjs/browser'

const config = useRuntimeConfig()

const handleSubmit = async () => {
  try {
    await emailjs.send(
      config.public.emailjsServiceId,
      config.public.emailjsTemplateId,
      {
        from_name: form.name,
        from_email: form.email,
        subject: form.subject,
        message: form.message,
      },
      {
        publicKey: config.public.emailjsPublicKey,
      }
    )

    submitted.value = true

    Object.assign(form, {
      name: '',
      email: '',
      subject: '',
      message: '',
    })

    setTimeout(() => {
      submitted.value = false
    }, 4000)
  } catch (error) {
    console.error(error)
    alert('Failed to send message.')
  }
}
const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: '',
})
const submitted = ref(false)

const contactLinks = [
  {
    icon: Mail,
    label: 'Email',
    value: 'shalsabillawahyuar@gmail.com',
    href: 'mailto:shalsabillawahyuar@gmail.com',
    external: false,
  },
  {
    icon: Briefcase,
    label: 'LinkedIn',
    value: 'shalsabilla-wahyu-5304692a9',
    href: 'https://www.linkedin.com/in/shalsabilla-wahyu-5304692a9/',
    external: true,
  },
  {
    icon: MapPin,
    label: 'Location',
    value: 'Surabaya, East Java, Indonesia',
    external: false,
  },
]

</script>
