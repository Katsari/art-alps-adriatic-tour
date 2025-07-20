<template>
  <div class="min-h-screen bg-gradient-to-br from-slate-50 via-blue-50/20 to-indigo-50/20">
    <Header />
    
    <div class="sticky top-0 z-40 bg-white/80 backdrop-blur-md shadow-sm mb-8">
      <div class="max-w-4xl mx-auto px-4 py-3">
        <div class="flex items-center justify-between text-sm">
          <span class="font-medium text-slate-700">The Smart Traveler's European Circuit</span>
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
        <ItineraryDay 
          v-for="(day, index) in itinerary" 
          :key="day.id"
          :day="day"
          :style="{ animationDelay: `${index * 100}ms` }"
          class="fade-slide-item"
        />
      </TransitionGroup>
    </main>

    <BudgetTracker :budget="budget" />
    
    <footer class="bg-slate-900 text-white py-8 px-4 text-center">
      <p class="text-sm opacity-80">Safe travels! Remember to check visa requirements and travel insurance.</p>
      <p class="text-xs mt-2 opacity-60">Budget calculations are estimates based on 2025 prices.</p>
    </footer>
  </div>
</template>

<script setup>
import { onMounted } from 'vue'
import Header from './components/Header.vue'
import BudgetTracker from './components/BudgetTracker.vue'
import ItineraryDay from './components/ItineraryDay.vue'
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