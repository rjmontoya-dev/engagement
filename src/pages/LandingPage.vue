<template>
  <main class="min-h-screen bg-[#f5e6f0] relative overflow-hidden">
    <!-- Floating Hearts Background Animation -->
    <FloatingHearts />
    
    <!-- Play Music Button -->
    <div class="absolute top-8 right-8 flex items-center gap-2 bg-white rounded-full px-6 py-3 shadow-sm hover:shadow-md transition-shadow cursor-pointer z-10">
      <span class="text-sm font-medium text-gray-800">🎵 Play Music 🎶</span>
    </div>

    <!-- Main Content Container -->
    <div class="min-h-screen flex flex-col items-center justify-center px-8 pb-32 relative z-10">

      <!-- The Start of Us Badge -->
      <div class="flex items-center gap-2 mb-8">
        <span class="text-gray-600">🤍</span>
        <span class="text-sm text-gray-600">The Start of Us</span>
      </div>

      <!-- Main Heading -->
      <h1 class="text-5xl md:text-6xl font-bold text-gray-900 text-center mb-6 leading-tight px-4">
        Hey [her name]... do you remember how it all started?
      </h1>

      <!-- Subtitle -->
      <p class="text-gray-500 text-center mb-12 max-w-2xl">
        Before I ask you something crazy... let's take a trip down memory lane 💕
      </p>

      <!-- Scroll Down Indicator -->
      <div class="flex flex-col items-center gap-2 mb-12">
        <div class="flex items-center gap-1 text-sm text-gray-400">
          <ChevronDown :size="20" />
          <span>Scroll Down</span>
        </div>
        <div class="flex gap-1">
          <span class="w-2 h-2 rounded-full bg-gray-300"></span>
          <span class="w-2 h-2 rounded-full bg-gray-300"></span>
          <span class="w-2 h-2 rounded-full bg-gray-400"></span>
        </div>
      </div>

      <!-- Ready Text -->
      <p class="text-gray-700 text-center mb-6 font-medium">
        Ready? Let's relive our adventure.
      </p>
    </div>

    <!-- Image Gallery Section -->
    <div class="absolute bottom-0 left-0 right-0 pb-8 z-10">
      <div class="flex gap-4 px-8 overflow-x-auto justify-center items-center scrollbar-hide">
        <div 
          v-for="(image, index) in memoryImages" 
          :key="index"
          class="flex-shrink-0 w-44 h-40 rounded-2xl overflow-hidden shadow-lg"
        >
          <img 
            :src="image.url" 
            :alt="image.alt" 
            class="w-full h-full object-cover"
          />
        </div>
      </div>
      <p class="text-center text-sm text-gray-400 mt-4 italic">
        A soft blur of our favorite moments—more to come as we scroll.
      </p>
    </div>
  </main>
</template>

<script setup>
import { ChevronDown } from 'lucide-vue-next'
import FloatingHearts from '../components/FloatingHearts.vue'

// Memory Images Gallery
const memoryImages = [
  {
    url: 'https://images.unsplash.com/photo-1441974231531-c6227db76b6e?w=400&h=400&fit=crop',
    alt: 'Memory 1'
  },
  {
    url: 'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?w=400&h=400&fit=crop',
    alt: 'Memory 2'
  },
  {
    url: 'https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=400&h=400&fit=crop',
    alt: 'Memory 3'
  },
  {
    url: 'https://images.unsplash.com/photo-1476514525535-07fb3b4ae5f1?w=400&h=400&fit=crop',
    alt: 'Memory 4'
  },
  {
    url: 'https://images.unsplash.com/photo-1511895426328-dc8714191300?w=400&h=400&fit=crop',
    alt: 'Memory 5'
  }
]
</script>

<style scoped>
/* Hide scrollbar for Chrome, Safari and Opera */
.scrollbar-hide::-webkit-scrollbar {
  display: none;
}

/* Hide scrollbar for IE, Edge and Firefox */
.scrollbar-hide {
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}
</style>
