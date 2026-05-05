<template>
  <div>
    <!-- Custom Cursor -->
    <div class="cursor-dot" ref="cursorDot" />
    <div class="cursor-ring" ref="cursorRing" :class="{ hovering: isHovering }" />

    <!-- Navigation -->
    <AppNav />

    <!-- Main Content -->
    <NuxtPage />

    <!-- Footer -->
    <AppFooter />
  </div>
</template>

<script setup>
const cursorDot = ref(null)
const cursorRing = ref(null)
const isHovering = ref(false)

onMounted(() => {
  const moveCursor = (e) => {
    if (cursorDot.value) {
      cursorDot.value.style.left = e.clientX + 'px'
      cursorDot.value.style.top = e.clientY + 'px'
    }
    if (cursorRing.value) {
      cursorRing.value.style.left = e.clientX + 'px'
      cursorRing.value.style.top = e.clientY + 'px'
    }
  }

  const handleHover = () => { isHovering.value = true }
  const handleLeave = () => { isHovering.value = false }

  window.addEventListener('mousemove', moveCursor)

  document.querySelectorAll('a, button, [data-hover]').forEach((el) => {
    el.addEventListener('mouseenter', handleHover)
    el.addEventListener('mouseleave', handleLeave)
  })

  // Intersection Observer for reveal animations
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible')
        }
      })
    },
    { threshold: 0.1 }
  )

  document.querySelectorAll('.reveal').forEach((el) => observer.observe(el))
})
</script>
