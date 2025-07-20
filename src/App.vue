<template>
  <div class="min-h-screen bg-gradient-to-br from-slate-50 via-blue-50/20 to-indigo-50/20">
    <Header />
    
    <div class="sticky top-0 z-40 bg-white/80 backdrop-blur-md shadow-sm mb-8">
      <div class="max-w-4xl mx-auto px-4 py-3">
        <div class="flex items-center justify-between text-sm">
          <span class="font-medium text-slate-700">The Smart Traveler's European Journey</span>
          <button @click="scrollToTop" class="flex items-center gap-2 text-blue-600 hover:text-blue-700 transition-colors cursor-pointer">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18"></path>
            </svg>
            Back to top
          </button>
        </div>
      </div>
    </div>
       
    <main class="max-w-4xl mx-auto px-4 pb-4">
      <TransitionGroup name="fade-slide" tag="div">
        <RouteMap 
          key="route-map"
          :style="{ animationDelay: '0ms' }"
          class="fade-slide-item"
        />
        <ItineraryDay 
          v-for="(day, index) in itinerary" 
          :key="day.id"
          :day="day"
          :style="{ animationDelay: `${(index + 1) * 100}ms` }"
          class="fade-slide-item"
        />
      </TransitionGroup>
    </main>

    <BudgetTracker :budget="budget" />
    
    <footer class="bg-slate-900 text-white py-12 px-4">
      <div class="max-w-4xl mx-auto">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 text-sm">
          <div>
            <h3 class="font-semibold mb-2 text-blue-400">Before You Go</h3>
            <ul class="space-y-1 text-slate-300">
              <li>✓ EU citizens: ID card sufficient</li>
              <li>✓ Most countries: 90 days visa-free</li>
              <li>✓ Travel insurance recommended</li>
            </ul>
          </div>
          <div>
            <h3 class="font-semibold mb-2 text-blue-400">Smart Travel Tips</h3>
            <ul class="space-y-1 text-slate-300">
              <li>✓ Book trains 2-3 weeks ahead</li>
              <li>✓ Hostels fill up in summer</li>
              <li>✓ Download offline maps</li>
            </ul>
          </div>
          <div>
            <h3 class="font-semibold mb-2 text-blue-400">Money Matters</h3>
            <ul class="space-y-1 text-slate-300">
              <li>✓ Croatia, Slovenia, Italy: Euro (€)</li>
              <li>✓ Switzerland: Swiss Franc (CHF)</li>
              <li>✓ Cards accepted almost everywhere</li>
            </ul>
          </div>
        </div>
        <div class="mt-8 pt-6 border-t border-slate-700 text-center">
          <p class="text-xs text-slate-400">Budget estimates based on 2025 prices • Prices may vary by season</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { onMounted } from 'vue'
import Header from './components/Header.vue'
import BudgetTracker from './components/BudgetTracker.vue'
import ItineraryDay from './components/ItineraryDay.vue'
import RouteMap from './components/RouteMap.vue'
import { itinerary, budget } from '../itineraryData.js'

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => {
  // Add scroll animations
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('show')
      }
    })
  }, { threshold: 0.1 })

  document.querySelectorAll('.fade-slide-item').forEach(el => {
    observer.observe(el)
  })
})
</script>

<style>
.fade-slide-item {
  opacity: 0;
  transform: translateY(20px);
  animation: fadeSlideIn 0.6s ease-out forwards;
}

@keyframes fadeSlideIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.5s ease;
}

.fade-slide-enter-from {
  opacity: 0;
  transform: translateY(30px);
}

.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}
</style>