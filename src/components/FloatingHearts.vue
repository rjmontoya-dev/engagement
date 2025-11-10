<template>
  <div class="floating-hearts-container">
    <div
      v-for="heart in hearts"
      :key="heart.id"
      class="heart"
      :style="{
        left: heart.left,
        animationDuration: heart.duration,
        animationDelay: heart.delay,
        fontSize: heart.size,
        opacity: heart.opacity
      }"
    >
      {{ heart.emoji }}
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const hearts = ref([])

// Heart emoji variations
const heartEmojis = ['💕', '💗', '💖', '💓', '❤️']

// Generate random hearts
const generateHearts = () => {
  const heartCount =4 // Number of hearts
  const generatedHearts = []

  for (let i = 0; i < heartCount; i++) {
    generatedHearts.push({
      id: i,
      emoji: heartEmojis[Math.floor(Math.random() * heartEmojis.length)],
      left: `${Math.random() * 100}%`,
      duration: `${8 + Math.random() * 10}s`, // 8-18 seconds
      delay: `${Math.random() * 5}s`, // 0-5 seconds delay
      size: `${1 + Math.random() * 2}rem`, // 1-3rem
      opacity: 0.2 + Math.random() * 0.4 // 0.2-0.6 opacity
    })
  }

  hearts.value = generatedHearts
}

onMounted(() => {
  generateHearts()
})
</script>

<style scoped>
.floating-hearts-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  pointer-events: none;
  z-index: 1;
}

.heart {
  position: absolute;
  bottom: -50px;
  animation: float-up linear infinite;
  filter: blur(0.5px);
}

@keyframes float-up {
  0% {
    bottom: -50px;
    transform: translateX(0) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: var(--heart-opacity, 0.5);
  }
  90% {
    opacity: var(--heart-opacity, 0.5);
  }
  100% {
    bottom: 110%;
    transform: translateX(calc(var(--drift, 0px))) rotate(360deg);
    opacity: 0;
  }
}

/* Add subtle horizontal drift */
.heart:nth-child(odd) {
  --drift: 50px;
}

.heart:nth-child(even) {
  --drift: -50px;
}

.heart:nth-child(3n) {
  --drift: 30px;
}

.heart:nth-child(4n) {
  --drift: -30px;
}
</style>
