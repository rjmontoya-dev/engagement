<template>
  <main class="min-h-screen bg-[#f5e6f0] relative overflow-hidden">
    <!-- Floating Hearts Background Animation -->
    <FloatingHearts />

    <!-- Header Section -->
    <header class="relative z-10 pt-8 px-8">
      <div class="flex justify-between items-start">
        <!-- Left: The Start of Us -->
        <div class="flex items-center gap-2">
          <span class="text-gray-600">🤍</span>
          <span class="text-sm text-gray-700 font-medium">The Start of Us</span>
        </div>

        <!-- Right: Music Player -->
        <div class="text-right">
          <div class="flex items-center gap-2 justify-end mb-1">
            <span class="text-sm">🎵</span>
            <span class="text-sm font-medium text-gray-800">Playing softly...</span>
          </div>
          <p class="text-xs text-gray-400">Soundtrack for our memories</p>
        </div>
      </div>
    </header>

    <!-- Main Content -->
    <div class="max-w-4xl mx-auto px-8 py-16 relative z-10">
      <!-- Chapter Badge -->
      <div class="flex items-center justify-center gap-2 mb-8">
        <span class="text-sm text-gray-600">⚙️</span>
        <span class="text-sm text-gray-600">Chapter 1 • the firsts</span>
      </div>

      <!-- Page Title -->
      <h1 class="text-5xl md:text-6xl font-bold text-gray-900 text-center mb-6">
        Where it all began
      </h1>

      <!-- Subtitle -->
      <p class="text-center text-gray-500 max-w-2xl mx-auto mb-16">
        Let's stroll through our sweetest "firsts" — the day we met, our first laugh, and that moment we knew this was something real.
      </p>

      <!-- Memory Cards -->
      <div class="space-y-6 mb-16">
        <!-- Card 1: Our First Hello -->
        <div 
          v-for="(memory, index) in memories" 
          :key="index"
          class="bg-white rounded-2xl shadow-md hover:shadow-lg transition-shadow p-6 flex gap-6 items-center"
        >
          <!-- Image -->
          <div class="flex-shrink-0 w-28 h-28 rounded-xl overflow-hidden">
            <img 
              :src="memory.image" 
              :alt="memory.title"
              class="w-full h-full object-cover"
            />
          </div>

          <!-- Content -->
          <div class="flex-1">
            <h3 class="text-xl font-bold text-gray-900 mb-2">{{ memory.title }}</h3>
            <p class="text-gray-600 text-sm mb-3">{{ memory.description }}</p>
            
            <!-- Meta Info -->
            <div class="flex items-center gap-4 text-xs text-gray-500">
              <div class="flex items-center gap-1">
                <component :is="memory.icon1" :size="14" />
                <span>{{ memory.meta1 }}</span>
              </div>
              <div class="flex items-center gap-1">
                <component :is="memory.icon2" :size="14" />
                <span>{{ memory.meta2 }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Navigation Buttons -->
      <div class="flex items-center justify-center gap-4">
        <button class="flex items-center gap-2 px-6 py-3 rounded-full bg-white text-gray-700 font-medium hover:bg-gray-50 transition-colors shadow-sm">
          <ChevronLeft :size="20" />
          <span>Back</span>
        </button>
        <button class="flex items-center gap-2 px-6 py-3 rounded-full bg-[#f4c4d0] text-gray-800 font-medium hover:bg-[#f0b0c2] transition-colors shadow-md">
          <span>Next Chapter</span>
          <ChevronRight :size="20" />
        </button>
      </div>

      <!-- Footer Text -->
      <p class="text-center text-xs text-gray-400 mt-8 italic">
        Chapter 1 of 3 — up next: The Little Things
      </p>
    </div>
  </main>
</template>

<script setup>
import { ChevronLeft, ChevronRight, MapPin, Calendar, Clock, Heart, Cloud, Music } from 'lucide-vue-next'
import FloatingHearts from '../components/FloatingHearts.vue'

// Memory data
const memories = [
  {
    title: 'Our First Hello',
    description: 'A coffee shop, a shy smile, and a feeling that stayed. You said hi, and the world got quieter.',
    image: 'https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=400&h=400&fit=crop',
    icon1: MapPin,
    meta1: 'Maple + Main Cafe',
    icon2: Calendar,
    meta2: 'Spring 20XX'
  },
//   {
//     title: 'First Date Stroll',
//     description: 'Sunset sidewalks and stories that didn\'t want to end.',
//     image: 'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?w=400&h=400&fit=crop',
//     icon1: Clock,
//     meta1: 'Golden hour',
//     icon2: Heart,
//     meta2: 'Butterflies'
//   },
//   {
//     title: 'First Laugh in the Rain',
//     description: 'We got soaked and didn\'t care — the kind of happy you don\'t forget.',
//     image: 'https://images.unsplash.com/photo-1518199266791-5375a83190b7?w=400&h=400&fit=crop',
//     icon1: Cloud,
//     meta1: 'Light drizzle',
//     icon2: Music,
//     meta2: 'Magic'
//   }
]
</script>

<style scoped>
/* Additional styles if needed */
</style>
