<template>
  <div class="bg-white rounded-xl shadow-lg overflow-hidden mb-8 transition-all duration-300 hover:shadow-xl">
    <div class="relative h-64 md:h-80 overflow-hidden bg-slate-200">
      <img 
        :src="getOptimizedImageUrl(day.imageUrl)" 
        :alt="day.title"
        class="w-full h-full object-cover transition-transform duration-700 hover:scale-110"
        loading="lazy"
      />
      <div class="absolute top-4 left-4 bg-white/90 backdrop-blur-sm px-4 py-2 rounded-full shadow-md">
        <span class="text-sm font-bold text-slate-700">{{ day.days }}</span>
      </div>
    </div>
    
    <div class="p-6 md:p-8">
      <h3 class="text-2xl md:text-3xl font-bold text-slate-800 mb-2">{{ day.title }}</h3>
      <p class="text-slate-700 text-base md:text-lg mb-6 leading-relaxed">{{ day.description }}</p>

      <!-- Budget Breakdown Section -->
      <div v-if="day.budgetBreakdown" class="bg-gradient-to-r from-blue-50 to-indigo-50 rounded-lg p-4 mb-6">
        <h5 class="font-semibold text-slate-800 mb-3 flex items-center gap-2">
          <CurrencyEuroIcon class="h-5 w-5 text-blue-600" />
          <span>Budget Breakdown</span>
        </h5>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-3 mb-3">
          <div class="text-center">
            <HomeModernIcon class="h-6 w-6 mx-auto mb-1 text-slate-600" />
            <p class="text-xs text-slate-600">Accommodation</p>
            <p class="font-bold text-slate-800">€{{ day.budgetBreakdown.accommodation }}</p>
          </div>
          <div class="text-center">
            <TruckIcon class="h-6 w-6 mx-auto mb-1 text-slate-600" />
            <p class="text-xs text-slate-600">Transport</p>
            <p class="font-bold text-slate-800">€{{ day.budgetBreakdown.transport }}</p>
          </div>
          <div class="text-center">
            <ShoppingBagIcon class="h-6 w-6 mx-auto mb-1 text-slate-600" />
            <p class="text-xs text-slate-600">Food</p>
            <p class="font-bold text-slate-800">€{{ day.budgetBreakdown.food }}</p>
          </div>
          <div class="text-center">
            <TicketIcon class="h-6 w-6 mx-auto mb-1 text-slate-600" />
            <p class="text-xs text-slate-600">Activities</p>
            <p class="font-bold text-slate-800">€{{ day.budgetBreakdown.activities }}</p>
          </div>
        </div>
        <div class="text-center pt-3 border-t border-blue-100">
          <p class="text-sm text-slate-600">Total for this destination</p>
          <p class="text-2xl font-bold text-blue-600">€{{ day.budgetBreakdown.total }}</p>
        </div>
      </div>

      <!-- Highlights Section -->
      <div v-if="day.highlights" class="mb-4">
        <button
          @click="showHighlights = !showHighlights"
          class="flex items-center gap-2 text-blue-600 hover:text-blue-700 font-medium mb-2 cursor-pointer"
        >
          <SparklesIcon class="h-5 w-5" />
          <span>Highlights</span>
          <ChevronDownIcon :class="['h-4 w-4 transition-transform', showHighlights ? 'rotate-180' : '']" />
        </button>
        <ul v-show="showHighlights" class="space-y-1 ml-2">
          <li v-for="highlight in day.highlights" :key="highlight" class="text-slate-600 text-base">
            • {{ highlight }}
          </li>
        </ul>
      </div>

      <!-- Budget Tips Section -->
      <div v-if="day.budgetTips" class="mb-4">
        <button 
          @click="showBudgetTips = !showBudgetTips"
          class="flex items-center gap-2 text-green-600 hover:text-green-700 font-medium mb-2 cursor-pointer"
        >
          <BanknotesIcon class="h-5 w-5" />
          <span>Budget Tips</span>
          <ChevronDownIcon :class="['h-4 w-4 transition-transform', showBudgetTips ? 'rotate-180' : '']" />
        </button>
        <ul v-show="showBudgetTips" class="space-y-1 ml-2">
          <li v-for="tip in day.budgetTips" :key="tip" class="text-slate-600 text-base">
            • {{ tip }}
          </li>
        </ul>
      </div>

      <!-- Detailed Itinerary Section -->
      <div v-if="day.detailedItinerary" class="mb-4">
        <button 
          @click="showItinerary = !showItinerary"
          class="flex items-center gap-2 text-purple-600 hover:text-purple-700 font-medium mb-2 cursor-pointer"
        >
          <CalendarDaysIcon class="h-5 w-5" />
          <span>Detailed Itinerary</span>
          <ChevronDownIcon :class="['h-4 w-4 transition-transform', showItinerary ? 'rotate-180' : '']" />
        </button>
        <div v-show="showItinerary" class="space-y-3 ml-2">
          <div v-for="(details, day) in day.detailedItinerary" :key="day">
            <h5 class="font-semibold text-slate-700 text-lg">{{ day }}</h5>
            <div class="text-slate-600 text-base leading-relaxed" v-html="formatDetails(details)"></div>
          </div>
        </div>
      </div>

      <!-- Route Map Section -->
      <div v-if="day.mapUrl" class="mb-4">
        <button 
          @click="showRouteMap = !showRouteMap"
          class="flex items-center gap-2 text-indigo-600 hover:text-indigo-700 font-medium mb-2 cursor-pointer"
        >
          <MapIcon class="h-5 w-5" />
          <span>Route Map</span>
          <ChevronDownIcon :class="['h-4 w-4 transition-transform', showRouteMap ? 'rotate-180' : '']" />
        </button>
        <div v-show="showRouteMap" class="ml-2">
          <div class="relative w-full h-[300px] sm:h-[400px] rounded-lg overflow-hidden bg-slate-100">
            <iframe
              :src="day.mapUrl"
              width="100%"
              height="100%"
              style="border:0;"
              allowfullscreen=""
              loading="lazy"
              referrerpolicy="no-referrer-when-downgrade"
              class="absolute inset-0"
            ></iframe>
          </div>
          <div v-if="day.routeUrl" class="mt-2">
            <a 
              :href="day.routeUrl" 
              target="_blank"
              rel="noopener noreferrer"
              class="inline-flex items-center gap-2 text-sm text-blue-600 hover:text-blue-700 transition-colors"
            >
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"></path>
              </svg>
              View full route with directions in Google Maps
            </a>
          </div>
        </div>
      </div>
      
      <div class="flex flex-wrap gap-3 pt-6">
        <a 
          :href="day.links.location" 
          target="_blank"
          rel="noopener noreferrer"
          class="flex items-center gap-2 px-4 py-2 bg-blue-50 text-blue-700 rounded-lg hover:bg-blue-100 transition-colors"
        >
          <MapPinIcon class="h-5 w-5" />
          <span class="font-medium">Location</span>
        </a>
        
        <a 
          :href="day.links.accommodation" 
          target="_blank"
          rel="noopener noreferrer"
          class="flex items-center gap-2 px-4 py-2 bg-green-50 text-green-700 rounded-lg hover:bg-green-100 transition-colors"
        >
          <HomeIcon class="h-5 w-5" />
          <span class="font-medium">Stay</span>
        </a>
        
        <a 
          :href="day.links.transport" 
          target="_blank"
          rel="noopener noreferrer"
          class="flex items-center gap-2 px-4 py-2 bg-purple-50 text-purple-700 rounded-lg hover:bg-purple-100 transition-colors"
        >
          <TruckIcon class="h-5 w-5" />
          <span class="font-medium">Transport</span>
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { MapPinIcon, HomeIcon, TruckIcon, SparklesIcon, BanknotesIcon, CalendarDaysIcon, ChevronDownIcon, CurrencyEuroIcon, HomeModernIcon, ShoppingBagIcon, TicketIcon, MapIcon } from '@heroicons/vue/24/outline'

defineProps({
  day: {
    type: Object,
    required: true
  }
})

const showHighlights = ref(false)
const showBudgetTips = ref(false)
const showItinerary = ref(false)
const showRouteMap = ref(false)

const getOptimizedImageUrl = (url) => {
  // For Unsplash images, add optimization parameters
  if (url.includes('unsplash.com')) {
    const baseUrl = url.split('?')[0]
    return `${baseUrl}?auto=compress&cs=tinysrgb&w=800&q=80`
  }
  // For Pexels images, add optimization parameters
  if (url.includes('pexels.com')) {
    const baseUrl = url.split('?')[0]
    return `${baseUrl}?auto=compress&cs=tinysrgb&w=800&h=600&q=80`
  }
  return url
}

const formatDetails = (details) => {
  // Convert text to bullet points
  let formatted = details
    .split('. ')
    .filter(sentence => sentence.trim())
    .map(sentence => {
      if (!sentence.endsWith('.')) sentence += '.'
      return `• ${sentence.trim()}`
    })
    .join('<br>')
  
  // Update price styling to be more subtle with gradient colors
  formatted = formatted.replace(
    /<span style='background-color: #FEE2E2; color: #DC2626; padding: 2px 6px; border-radius: 4px; font-weight: 600; font-size: 0.9em; display: inline-block; margin: 0 2px;'>([^<]+)<\/span>/g,
    (match, price) => {
      // Extract numeric value
      const numericValue = parseFloat(price.replace(/[€CHF]/g, '').split('-')[0])
      
      let bgColor, textColor
      if (numericValue <= 10) {
        // Low prices: yellow/amber
        bgColor = '#FEF3C7'
        textColor = '#92400E'
      } else if (numericValue <= 25) {
        // Medium prices: orange
        bgColor = '#FED7AA'
        textColor = '#9A3412'
      } else {
        // High prices: red (more subtle)
        bgColor = '#FECACA'
        textColor = '#991B1B'
      }
      
      return `<span style='background-color: ${bgColor}; color: ${textColor}; padding: 1px 4px; border-radius: 3px; font-weight: 500; font-size: 0.875em; display: inline-block; margin: 0 2px;'>${price}</span>`
    }
  )
  
  return formatted
}
</script>