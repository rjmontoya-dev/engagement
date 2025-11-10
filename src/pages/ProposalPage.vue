<template>
  <main class="min-h-screen bg-[#d4c4c0] relative overflow-hidden py-12 px-6">
    <!-- Floating Hearts Background Animation -->
    <FloatingHearts />

    <!-- Confetti Canvas -->
    <canvas ref="confettiCanvas" class="fixed inset-0 pointer-events-none z-50"></canvas>

    <!-- Success Message Overlay -->
    <transition name="fade">
      <div v-if="showSuccessMessage" class="fixed inset-0 flex items-center justify-center z-40 bg-black/30 backdrop-blur-sm">
        <div class="bg-white rounded-3xl shadow-2xl p-12 mx-4 max-w-md text-center animate-scale-in">
          <div class="text-6xl mb-4">💕</div>
          <h2 class="text-3xl font-bold text-gray-900 mb-4">
            You just made me the happiest person alive.
          </h2>
          <p class="text-gray-500">Preparing something special for you...</p>
        </div>
      </div>
    </transition>

    <!-- Content Container -->
    <div class="max-w-3xl mx-auto relative z-10 space-y-8">
      <!-- Top Card: The Moment -->
      <div class="bg-white rounded-3xl shadow-xl p-12 text-center">
        <!-- Badge -->
        <div class="flex items-center justify-center gap-2 mb-6">
          <span class="text-sm text-gray-600">⚙️</span>
          <span class="text-sm text-gray-600">The Moment</span>
        </div>

        <!-- Title -->
        <h1 class="text-4xl md:text-5xl font-bold text-gray-900 mb-4">
          And now... here we are.
        </h1>

        <!-- Subtitle -->
        <p class="text-gray-500">
          After every laugh, every memory, every moment — I know one thing for sure.
        </p>
      </div>

      <!-- Main Proposal Card -->
      <div class="bg-white rounded-3xl shadow-xl p-12">
        <!-- The Big Question -->
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 text-center mb-8">
          [Her Name], will you marry me?
        </h2>

        <!-- Action Buttons -->
        <div class="flex items-center justify-center gap-4 mb-6 relative min-h-[60px]">
          <!-- Playful "No" Button -->
          <button 
            ref="noButton"
            @mouseenter="moveNoButton"
            @click="moveNoButton"
            :style="{ 
              position: noButtonMoved ? 'fixed' : 'relative',
              left: noButtonMoved ? `${noButtonPosition.x}px` : 'auto',
              top: noButtonMoved ? `${noButtonPosition.y}px` : 'auto',
              transition: 'all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55)'
            }"
            class="bg-[#f4c4d0] hover:bg-[#f0b0c2] text-gray-800 font-medium px-8 py-3 rounded-full shadow-md hover:shadow-lg flex items-center gap-2 z-20 relative"
          >
            <Gift :size="18" />
            <span>No 😅</span>
            
            <!-- Tooltip -->
            <transition name="tooltip">
              <div v-if="showTooltip" class="absolute -top-12 left-1/2 transform -translate-x-1/2 bg-gray-900 text-white text-sm px-4 py-2 rounded-lg whitespace-nowrap pointer-events-none z-30">
                {{ currentTooltip }}
                <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 translate-y-1/2 rotate-45 w-2 h-2 bg-gray-900"></div>
              </div>
            </transition>
          </button>

          <!-- Growing "Yes" Button -->
          <button 
            @click="handleYesClick"
            :style="{ 
              transform: `scale(${yesButtonScale})`,
              boxShadow: yesButtonScale > 1 ? '0 0 30px rgba(244, 196, 208, 0.8)' : ''
            }"
            class="bg-white hover:bg-gray-50 text-gray-800 font-medium px-8 py-3 rounded-full border-2 border-gray-200 hover:border-[#f4c4d0] transition-all flex items-center gap-2 yes-button"
          >
            <Heart :size="18" class="text-[#f4c4d0]" />
            <span>Of Course I Will 💗</span>
          </button>
        </div>

        <!-- Subtle Quote -->
        <p class="text-center text-sm text-gray-400 italic mb-8">
          "No matter where life takes us, I'll always choose you."
        </p>

        <!-- Image Gallery -->
        <div class="grid grid-cols-2 gap-4 mb-6">
          <div class="relative rounded-2xl overflow-hidden shadow-lg aspect-[4/3]">
            <img 
              src="https://images.unsplash.com/photo-1518568814500-bf0f8d125f46?w=600&h=450&fit=crop"
              alt="Proposal moment"
              class="w-full h-full object-cover"
            />
            <div class="absolute bottom-3 left-1/2 transform -translate-x-1/2">
              <div class="bg-white/20 backdrop-blur-sm rounded-full px-4 py-1">
                <span class="text-white text-xs font-medium">Our moment</span>
              </div>
            </div>
          </div>
          <div class="relative rounded-2xl overflow-hidden shadow-lg aspect-[4/3]">
            <img 
              src="https://images.unsplash.com/photo-1513710239666-c29e2c09b7f2?w=600&h=450&fit=crop"
              alt="Celebration"
              class="w-full h-full object-cover"
            />
            <div class="absolute bottom-3 left-1/2 transform -translate-x-1/2">
              <div class="bg-white/20 backdrop-blur-sm rounded-full px-4 py-1">
                <span class="text-white text-xs font-medium">Forever</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Waiting Text -->
        <p class="text-center text-sm text-gray-400 italic">
          My heart is racing for your answer...
        </p>
      </div>

      <!-- Bottom Card: Forever Starts Today -->
      <div class="bg-white rounded-3xl shadow-xl p-10 text-center">
        <h3 class="text-2xl font-bold text-gray-900 mb-6">
          Forever starts today.
        </h3>

        <!-- Action Buttons -->
        <div class="flex flex-col sm:flex-row items-center justify-center gap-4 mb-8">
          <button class="bg-[#f4c4d0] hover:bg-[#f0b0c2] text-gray-800 font-medium px-6 py-3 rounded-full shadow-md hover:shadow-lg transition-all flex items-center gap-2 w-full sm:w-auto justify-center">
            <Video :size="18" />
            <span>Watch Our Story Video 🎬</span>
          </button>
          <button class="bg-white hover:bg-gray-50 text-gray-800 font-medium px-6 py-3 rounded-full border-2 border-gray-200 hover:border-gray-300 transition-all flex items-center gap-2 w-full sm:w-auto justify-center">
            <Sparkles :size="18" />
            <span>See What's Next 💗</span>
          </button>
        </div>

        <!-- Footer Text -->
        <p class="text-xs text-gray-400">
          Soft music fades in
        </p>
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { Gift, Heart, Video, Sparkles } from 'lucide-vue-next'
import FloatingHearts from '../components/FloatingHearts.vue'

// Reactive state
const noButton = ref(null)
const confettiCanvas = ref(null)
const noButtonMoved = ref(false)
const noButtonPosition = ref({ x: 0, y: 0 })
const showTooltip = ref(false)
const currentTooltip = ref('')
const yesButtonScale = ref(1)
const noButtonAvoidCount = ref(0)
const showSuccessMessage = ref(false)

// Playful tooltips
const tooltips = [
  "Hey, why are you clicking this? 😏",
  "This button's broken 😜",
  "Are you sure about that? 🤔",
  "Wrong button! Try again 💕",
  "Really? You're breaking my heart 💔",
  "The other button looks lonely 👀",
  "Nice try! 😄",
  "You can't catch me! 🏃",
]

// Move "No" button to random position
const moveNoButton = () => {
  const maxX = window.innerWidth - 200
  const maxY = window.innerHeight - 100
  const minX = 100
  const minY = 100

  noButtonPosition.value = {
    x: Math.random() * (maxX - minX) + minX,
    y: Math.random() * (maxY - minY) + minY
  }

  noButtonMoved.value = true
  noButtonAvoidCount.value++

  // Grow the "Yes" button each time "No" is avoided
  yesButtonScale.value = Math.min(1 + (noButtonAvoidCount.value * 0.15), 1.6)

  // Show random tooltip
  currentTooltip.value = tooltips[Math.floor(Math.random() * tooltips.length)]
  showTooltip.value = true
}

// Confetti animation
const createConfetti = () => {
  const canvas = confettiCanvas.value
  if (!canvas) return

  const ctx = canvas.getContext('2d')
  canvas.width = window.innerWidth
  canvas.height = window.innerHeight

  const particles = []
  const colors = ['#ff69b4', '#ff1493', '#ffc0cb', '#ffb6c1', '#ff69b4', '#db7093']
  const shapes = ['heart', 'circle']

  // Create particles
  for (let i = 0; i < 150; i++) {
    particles.push({
      x: Math.random() * canvas.width,
      y: -10 - Math.random() * canvas.height,
      size: Math.random() * 8 + 4,
      speedY: Math.random() * 3 + 2,
      speedX: Math.random() * 2 - 1,
      color: colors[Math.floor(Math.random() * colors.length)],
      shape: shapes[Math.floor(Math.random() * shapes.length)],
      rotation: Math.random() * 360,
      rotationSpeed: Math.random() * 4 - 2
    })
  }

  // Animation loop
  const animate = () => {
    ctx.clearRect(0, 0, canvas.width, canvas.height)

    particles.forEach((p, index) => {
      ctx.save()
      ctx.translate(p.x, p.y)
      ctx.rotate((p.rotation * Math.PI) / 180)

      if (p.shape === 'heart') {
        // Draw heart
        ctx.fillStyle = p.color
        ctx.beginPath()
        ctx.moveTo(0, p.size / 4)
        ctx.bezierCurveTo(-p.size / 2, -p.size / 4, -p.size, p.size / 4, 0, p.size)
        ctx.bezierCurveTo(p.size, p.size / 4, p.size / 2, -p.size / 4, 0, p.size / 4)
        ctx.fill()
      } else {
        // Draw circle
        ctx.fillStyle = p.color
        ctx.beginPath()
        ctx.arc(0, 0, p.size / 2, 0, Math.PI * 2)
        ctx.fill()
      }

      ctx.restore()

      // Update position
      p.y += p.speedY
      p.x += p.speedX
      p.rotation += p.rotationSpeed

      // Remove if off screen
      if (p.y > canvas.height) {
        particles.splice(index, 1)
      }
    })

    if (particles.length > 0) {
      requestAnimationFrame(animate)
    }
  }

  animate()
}

// Handle "Yes" button click
const handleYesClick = () => {
  showSuccessMessage.value = true
  createConfetti()

  // Wait 4 seconds then transition to next page
  setTimeout(() => {
    // TODO: Add navigation to wedding date picker page
    console.log('Navigate to wedding date picker...')
  }, 4000)
}

// Cleanup
onMounted(() => {
  window.addEventListener('resize', () => {
    if (confettiCanvas.value) {
      confettiCanvas.value.width = window.innerWidth
      confettiCanvas.value.height = window.innerHeight
    }
  })
})
</script>

<style scoped>
/* Yes button pulsing heartbeat animation */
.yes-button {
  animation: heartbeat 1.5s ease-in-out infinite;
}

@keyframes heartbeat {
  0%, 100% {
    transform: scale(1);
  }
  10% {
    transform: scale(1.05);
  }
  20% {
    transform: scale(1);
  }
}

/* Sparkle effect for yes button */
.yes-button:hover {
  animation: heartbeat 1.5s ease-in-out infinite, sparkle 2s ease-in-out infinite;
}

@keyframes sparkle {
  0%, 100% {
    filter: brightness(1);
  }
  50% {
    filter: brightness(1.2);
  }
}

/* Tooltip animation */
.tooltip-enter-active, .tooltip-leave-active {
  transition: all 0.3s ease;
}

.tooltip-enter-from, .tooltip-leave-to {
  opacity: 0;
  transform: translateX(-50%) translateY(-5px);
}

/* Success message fade and scale animation */
.fade-enter-active, .fade-leave-active {
  transition: all 0.5s ease;
}

.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

@keyframes scale-in {
  0% {
    transform: scale(0.8);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

.animate-scale-in {
  animation: scale-in 0.5s ease-out;
}
</style>
