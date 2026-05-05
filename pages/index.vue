<template>
  <main>
    <HeroSection />
    <AboutSection />
    <ExperienceSection />
    <SkillsSection />
    <ProjectsSection />
    <ImageCarousel />
    <ContactSection />
  </main>
</template>

<script setup>
useHead({
  title: 'Shalsabilla Wahyu — Frontend Developer & UI/UX Designer',
})

// Re-run intersection observer after page mounts (for dynamic reveals)
onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible')
        }
      })
    },
    { threshold: 0.08, rootMargin: '0px 0px -60px 0px' }
  )

  // Small delay to let components render
  setTimeout(() => {
    document.querySelectorAll('.reveal').forEach((el) => observer.observe(el))
  }, 100)
})
</script>
