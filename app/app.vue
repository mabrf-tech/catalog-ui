<template>
  <div class="min-h-screen bg-gradient-to-br from-slate-900 via-slate-800 to-slate-900">
    <NuxtRouteAnnouncer />
    
    <!-- Header -->
    <header
      class="fixed inset-x-0 top-0 px-4 py-6 z-20 transition-colors duration-300"
      :class="isScrolled ? 'bg-slate-900/80 backdrop-blur-md border-b border-slate-800/60' : 'bg-transparent'"
    >
      <div class="container mx-auto flex items-center justify-between">
        <div class="text-2xl font-bold text-white">
          <span class="text-green-500">WYN</span> Scout
        </div>
        <nav class="hidden md:flex gap-6">
          <a href="#highlights" class="text-gray-300 hover:text-white transition-colors">Highlights</a>
          <a href="#pricing" class="text-gray-300 hover:text-white transition-colors">Pricing</a>
          <a href="#contact" class="text-gray-300 hover:text-white transition-colors">Contact</a>
        </nav>
      </div>
    </header>

    <!-- Video Hero Section -->
    <section class="relative h-screen w-full overflow-hidden">
      <div class="absolute inset-0 overflow-hidden pointer-events-none">
        <iframe
          class="absolute top-1/2 left-1/2 min-w-full min-h-full w-auto h-auto -translate-x-1/2 -translate-y-1/2 aspect-video"
          src="https://www.youtube.com/embed/aZsicM8i_OI?autoplay=1&mute=1&loop=1&playlist=aZsicM8i_OI&controls=0&modestbranding=1&rel=0&start=7"
          title="WYN Scout"
          frameborder="0"
          allow="autoplay; fullscreen; picture-in-picture"
          allowfullscreen
        ></iframe>
      </div>
      <div class="absolute inset-0 bg-black/60"></div>
      <div class="relative z-10 flex h-full items-center justify-center">
        <div class="text-center space-y-4">
          <h1 class="text-5xl md:text-9xl font-extrabold tracking-wide text-white/50 drop-shadow-lg">
            <span class="text-green-500/50">WYN</span> Scout
          </h1>
          <p class="text-xl md:text-3xl text-white/50 font-extrabold tracking-wide">
            Your best move
          </p>
        </div>
      </div>
    </section>

    <!-- Hero Section with Carousel -->
    <section id="highlights" class="container mx-auto px-4 py-12">
      <div class="text-center mb-12">
        <h1 class="text-5xl md:text-6xl font-bold text-white mb-4">
          Game Highlights
          <span class="block text-green-500">Media Catalog</span>
        </h1>
        <p class="text-xl text-gray-300 max-w-2xl mx-auto">
          Access professional photos and videos from your favorite soccer matches. 
          Capture every moment, every goal, every victory.
        </p>
      </div>

      <!-- Carousel -->
      <div class="relative max-w-6xl mx-auto">
        <div class="overflow-hidden rounded-2xl shadow-2xl">
          <div 
            class="flex transition-transform duration-500 ease-in-out"
            :style="{ transform: `translateX(-${currentSlide * 100}%)` }"
          >
            <div 
              v-for="(slide, index) in carouselSlides" 
              :key="index"
              class="min-w-full relative"
            >
              <div class="relative h-[500px] md:h-[600px] bg-gradient-to-br from-green-600 to-green-800">
                <!-- Placeholder for video/image -->
                <div class="absolute inset-0 flex items-center justify-center">
                  <div class="text-center text-white">
                    <div class="text-6xl mb-4">⚽</div>
                    <h3 class="text-3xl font-bold mb-2">{{ slide.title }}</h3>
                    <p class="text-xl opacity-90">{{ slide.description }}</p>
                  </div>
                </div>
                <!-- Overlay gradient -->
                <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-black/20 to-transparent"></div>
              </div>
            </div>
          </div>
        </div>

        <!-- Carousel Navigation -->
        <button
          @click="previousSlide"
          class="absolute left-4 top-1/2 -translate-y-1/2 bg-white/20 hover:bg-white/30 backdrop-blur-sm text-white p-3 rounded-full transition-all duration-200"
          aria-label="Previous slide"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
          </svg>
        </button>
        <button
          @click="nextSlide"
          class="absolute right-4 top-1/2 -translate-y-1/2 bg-white/20 hover:bg-white/30 backdrop-blur-sm text-white p-3 rounded-full transition-all duration-200"
          aria-label="Next slide"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
        </button>

        <!-- Carousel Indicators -->
        <div class="flex justify-center gap-2 mt-6">
          <button
            v-for="(slide, index) in carouselSlides"
            :key="index"
            @click="currentSlide = index"
            class="h-2 rounded-full transition-all duration-200"
            :class="currentSlide === index ? 'w-8 bg-green-500' : 'w-2 bg-white/30'"
            :aria-label="`Go to slide ${index + 1}`"
          />
        </div>
      </div>
    </section>

    <!-- Pricing Section -->
    <section id="pricing" class="container mx-auto px-4 py-16">
      <div class="text-center mb-12">
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-4">
          Choose Your Plan
        </h2>
        <p class="text-xl text-gray-300">
          Flexible pricing options for every fan
        </p>
      </div>

      <div class="grid md:grid-cols-3 gap-8 max-w-5xl mx-auto">
        <!-- Individual Video Plan -->
        <div class="bg-slate-800/50 backdrop-blur-sm rounded-2xl p-8 border border-slate-700 hover:border-green-500 transition-all duration-300 hover:shadow-2xl hover:shadow-green-500/20">
          <div class="text-center">
            <h3 class="text-2xl font-bold text-white mb-2">Individual Video</h3>
            <div class="my-6">
              <span class="text-5xl font-bold text-white">R$ 5,99</span>
              <p class="text-gray-400 mt-2">per video</p>
            </div>
            <ul class="text-left space-y-3 mb-8 text-gray-300">
              <li class="flex items-start">
                <svg class="w-5 h-5 text-green-500 mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span>Single video download</span>
              </li>
              <li class="flex items-start">
                <svg class="w-5 h-5 text-green-500 mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span>HD quality</span>
              </li>
              <li class="flex items-start">
                <svg class="w-5 h-5 text-green-500 mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span>Instant access</span>
              </li>
            </ul>
            <button class="w-full bg-slate-700 hover:bg-slate-600 text-white font-semibold py-3 px-6 rounded-lg transition-colors duration-200">
              Buy Now
            </button>
          </div>
        </div>

        <!-- Monthly Plan -->
        <div class="bg-gradient-to-br from-green-600 to-green-700 rounded-2xl p-8 border-2 border-green-500 shadow-2xl shadow-green-500/30 transform scale-105 relative">
          <div class="absolute top-0 right-0 bg-green-500 text-white px-4 py-1 rounded-bl-lg rounded-tr-2xl text-sm font-semibold">
            POPULAR
          </div>
          <div class="text-center">
            <h3 class="text-2xl font-bold text-white mb-2">Monthly Plan</h3>
            <div class="my-6">
              <span class="text-5xl font-bold text-white">R$ 24,99</span>
              <p class="text-white/80 mt-2">per month</p>
            </div>
            <ul class="text-left space-y-3 mb-8 text-white/90">
              <li class="flex items-start">
                <svg class="w-5 h-5 text-white mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span><strong>Unlimited downloads</strong></span>
              </li>
              <li class="flex items-start">
                <svg class="w-5 h-5 text-white mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span>HD & 4K quality</span>
              </li>
              <li class="flex items-start">
                <svg class="w-5 h-5 text-white mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span>All matches included</span>
              </li>
              <li class="flex items-start">
                <svg class="w-5 h-5 text-white mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span>Cancel anytime</span>
              </li>
            </ul>
            <button class="w-full bg-white hover:bg-gray-100 text-green-600 font-semibold py-3 px-6 rounded-lg transition-colors duration-200">
              Subscribe Now
            </button>
          </div>
        </div>

        <!-- Yearly Plan -->
        <div class="bg-slate-800/50 backdrop-blur-sm rounded-2xl p-8 border border-slate-700 hover:border-green-500 transition-all duration-300 hover:shadow-2xl hover:shadow-green-500/20">
          <div class="text-center">
            <h3 class="text-2xl font-bold text-white mb-2">Yearly Plan</h3>
            <div class="my-6">
              <span class="text-5xl font-bold text-white">R$ 19,99</span>
              <p class="text-gray-400 mt-2">per month</p>
              <p class="text-sm text-green-500 mt-1">Billed as 12 x R$ 19,99</p>
            </div>
            <ul class="text-left space-y-3 mb-8 text-gray-300">
              <li class="flex items-start">
                <svg class="w-5 h-5 text-green-500 mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span><strong>Unlimited downloads</strong></span>
              </li>
              <li class="flex items-start">
                <svg class="w-5 h-5 text-green-500 mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span>HD & 4K quality</span>
              </li>
              <li class="flex items-start">
                <svg class="w-5 h-5 text-green-500 mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span>All matches included</span>
              </li>
              <li class="flex items-start">
                <svg class="w-5 h-5 text-green-500 mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span>Save 20% vs monthly</span>
              </li>
            </ul>
            <button class="w-full bg-green-600 hover:bg-green-700 text-white font-semibold py-3 px-6 rounded-lg transition-colors duration-200">
              Subscribe Now
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer id="contact" class="container mx-auto px-4 py-12 border-t border-slate-700">
      <div class="text-center text-gray-400">
        <p class="mb-2">© 2025 WYN Scout. All rights reserved.</p>
        <p>Professional Soccer Player Management</p>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const currentSlide = ref(0)
const isScrolled = ref(false)

const carouselSlides = [
  {
    title: 'Match Highlights',
    description: 'Professional game footage and key moments'
  },
  {
    title: 'Player Actions',
    description: 'Individual player performances and skills'
  },
  {
    title: 'Goal Celebrations',
    description: 'Capture every goal and celebration moment'
  },
  {
    title: 'Training Sessions',
    description: 'Behind-the-scenes training content'
  }
]

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % carouselSlides.length
}

const previousSlide = () => {
  currentSlide.value = currentSlide.value === 0 ? carouselSlides.length - 1 : currentSlide.value - 1
}

let autoSlideInterval: ReturnType<typeof setInterval> | null = null

const handleScroll = () => {
  isScrolled.value = window.scrollY > 10
}

onMounted(() => {
  // Auto-advance carousel every 5 seconds
  autoSlideInterval = setInterval(() => {
    nextSlide()
  }, 5000)

  window.addEventListener('scroll', handleScroll, { passive: true })
  handleScroll()
})

onUnmounted(() => {
  if (autoSlideInterval) {
    clearInterval(autoSlideInterval)
  }
  window.removeEventListener('scroll', handleScroll)
})
</script>
