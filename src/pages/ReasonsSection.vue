<template>
  <main class="min-h-screen bg-[#f5e6f0] relative overflow-hidden py-12 px-6">
    <!-- Floating Hearts Background Animation -->
    <FloatingHearts />

    <!-- Content Container -->
    <div class="max-w-2xl mx-auto relative z-10">
      <!-- Header Badge -->
      <div class="flex items-center justify-center gap-2 mb-6">
        <span class="text-sm text-gray-600">⚙️</span>
        <span class="text-sm text-gray-600">With all my heart</span>
      </div>

      <!-- Main Title -->
      <h1 class="text-4xl md:text-5xl font-bold text-gray-900 text-center mb-3">
        Reasons Why I Want to Marry You 💍
      </h1>

      <!-- Subtitle -->
      <p class="text-center text-gray-500 mb-12">
        It's more than love — it's everything you are.
      </p>

      <!-- Masonry Grid Layout -->
      <div class="grid grid-cols-2 gap-4 mb-12">
        <!-- Item 1: Large Image (spans full width) -->
        <div class="col-span-2">
          <div class="relative rounded-3xl overflow-hidden shadow-lg aspect-[3/4] bg-black">
            <img 
              src="https://images.unsplash.com/photo-1518199266791-5375a83190b7?w=600&h=800&fit=crop"
              alt="Heart hands"
              class="w-full h-full object-cover"
            />
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2">
              <div class="bg-white/20 backdrop-blur-sm rounded-full px-6 py-2">
                <span class="text-white text-sm font-medium">Reason #1</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Item 2: Text Card (left) -->
        <div class="col-span-1">
          <div class="bg-white rounded-3xl shadow-lg p-6 h-full flex flex-col justify-center">
            <div class="mb-3">
              <span class="text-2xl">😊</span>
            </div>
            <h3 class="text-lg font-bold text-gray-900 mb-2">Your laugh is my favorite sound</h3>
            <p class="text-sm text-gray-600 leading-relaxed">
              It turns ordinary moments into memories and reminds me how lucky I am.
            </p>
          </div>
        </div>

        <!-- Item 3: Tall Image (right) -->
        <div class="col-span-1 row-span-2">
          <div class="relative rounded-3xl overflow-hidden shadow-lg h-full bg-gray-200">
            <img 
              src="https://images.unsplash.com/photo-1516589178581-6cd7833ae3b2?w=400&h=700&fit=crop"
              alt="Couple together"
              class="w-full h-full object-cover"
            />
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2">
              <div class="bg-white/20 backdrop-blur-sm rounded-full px-6 py-2">
                <span class="text-white text-sm font-medium">Reason #2</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Item 4: Medium Image (left) -->
        <div class="col-span-1">
          <div class="relative rounded-3xl overflow-hidden shadow-lg aspect-[4/5] bg-gray-300">
            <img 
              src="https://images.unsplash.com/photo-1501959915551-4e8d30928317?w=400&h=500&fit=crop"
              alt="Cozy moment"
              class="w-full h-full object-cover"
            />
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2">
              <div class="bg-white/20 backdrop-blur-sm rounded-full px-6 py-2">
                <span class="text-white text-sm font-medium">Reason #3</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Item 5: Text Card (spans full width) -->
        <div class="col-span-2">
          <div class="bg-white rounded-3xl shadow-lg p-6">
            <h3 class="text-lg font-bold text-gray-900 mb-2">You light up my world</h3>
            <p class="text-sm text-gray-600 leading-relaxed">
              Your warmth and wonder make the smallest days feel extraordinary.
            </p>
          </div>
        </div>

        <!-- Item 6: Wide Image (spans full width) -->
        <div class="col-span-2">
          <div class="relative rounded-3xl overflow-hidden shadow-lg aspect-[16/9] bg-black">
            <img 
              src="https://images.unsplash.com/photo-1519681393784-d120267933ba?w=800&h=450&fit=crop"
              alt="City lights"
              class="w-full h-full object-cover"
            />
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2">
              <div class="bg-white/20 backdrop-blur-sm rounded-full px-6 py-2">
                <span class="text-white text-sm font-medium">Reason #4</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Item 7: Medium Image (left) -->
        <div class="col-span-1">
          <div class="relative rounded-3xl overflow-hidden shadow-lg aspect-square bg-green-200">
            <img 
              src="https://images.unsplash.com/photo-1522673607211-8c4b5b4b7c2a?w=400&h=400&fit=crop"
              alt="Holding hands"
              class="w-full h-full object-cover"
            />
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2">
              <div class="bg-white/20 backdrop-blur-sm rounded-full px-6 py-2">
                <span class="text-white text-sm font-medium">Reason #5</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Item 8: Text Card (right) -->
        <div class="col-span-1">
          <div class="bg-white rounded-3xl shadow-lg p-6 h-full flex flex-col justify-center">
            <h3 class="text-lg font-bold text-gray-900 mb-2">We share a rhythm</h3>
            <p class="text-sm text-gray-600 leading-relaxed">
              From quiet mornings to late-night drives, our soundtrack always finds its way back to us.
            </p>
          </div>
        </div>

        <!-- Item 9: Medium Image (left) -->
        <div class="col-span-1">
          <div class="relative rounded-3xl overflow-hidden shadow-lg aspect-[4/5] bg-gray-400">
            <img 
              src="https://images.unsplash.com/photo-1484980972926-edee96e0960d?w=400&h=500&fit=crop"
              alt="Cozy room"
              class="w-full h-full object-cover"
            />
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2">
              <div class="bg-white/20 backdrop-blur-sm rounded-full px-6 py-2">
                <span class="text-white text-sm font-medium">Reason #6</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Item 10: Medium Image (right) -->
        <div class="col-span-1">
          <div class="relative rounded-3xl overflow-hidden shadow-lg aspect-[4/5] bg-orange-200">
            <img 
              src="https://images.unsplash.com/photo-1495616811223-4d98c6e9c869?w=400&h=500&fit=crop"
              alt="Sunset"
              class="w-full h-full object-cover"
            />
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2">
              <div class="bg-white/20 backdrop-blur-sm rounded-full px-6 py-2">
                <span class="text-white text-sm font-medium">Reason #7</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Item 11: Text Card (left) -->
        <div class="col-span-1">
          <div class="bg-white rounded-3xl shadow-lg p-6 h-full flex flex-col justify-center">
            <h3 class="text-lg font-bold text-gray-900 mb-2">You're my favorite adventure</h3>
            <p class="text-sm text-gray-600 leading-relaxed">
              With you, the unknown doesn't feel scary, every detour — it's purely together.
            </p>
          </div>
        </div>

        <!-- Item 12: Medium Image (right) -->
        <div class="col-span-1">
          <div class="relative rounded-3xl overflow-hidden shadow-lg aspect-square bg-green-300">
            <img 
              src="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=400&h=400&fit=crop"
              alt="Mountain adventure"
              class="w-full h-full object-cover"
            />
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2">
              <div class="bg-white/20 backdrop-blur-sm rounded-full px-6 py-2">
                <span class="text-white text-sm font-medium">Reason #8</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Quote Section -->
      <div class="text-center mb-8">
        <p class="text-gray-700 text-lg italic mb-2">
          "You're my home, my calm, and my adventure all at once."
        </p>
        <p class="text-gray-500 text-sm mb-8">
          But there's one more reason I want to tell you...
        </p>
      </div>

      <!-- The Big Question Button -->
      <div class="flex justify-center">
        <button class="bg-[#f4c4d0] hover:bg-[#f0b0c2] text-gray-800 font-medium px-8 py-4 rounded-full shadow-lg hover:shadow-xl transition-all flex items-center gap-2">
          <span>The Big Question</span>
          <ChevronRight :size="20" />
        </button>
      </div>
    </div>
  </main>
</template>

<script setup>
import { ChevronRight } from 'lucide-vue-next'
import FloatingHearts from '../components/FloatingHearts.vue'
</script>

<style scoped>
/* Additional styles if needed */
</style>
