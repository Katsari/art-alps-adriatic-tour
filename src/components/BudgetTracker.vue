<template>
  <div class="max-w-4xl mx-auto px-4 mb-12">
    <div class="bg-gradient-to-br from-white via-blue-50/30 to-indigo-50/30 rounded-2xl shadow-xl p-8 backdrop-blur-sm border border-blue-100">
      <h2 class="text-3xl font-bold mb-8 text-center bg-gradient-to-r from-blue-600 to-indigo-600 bg-clip-text text-transparent">
        Total Budget Breakdown
      </h2>
      
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
        <div v-for="(item, index) in budget.breakdown" :key="item.category" 
             class="bg-white rounded-xl p-6 text-center shadow-lg hover:shadow-xl transition-all hover:scale-105 border border-blue-50">
          <div class="mb-3" v-html="getCategoryIcon(item.category)"></div>
          <h3 class="text-sm font-medium text-slate-600 mb-2">{{ item.category }}</h3>
          <p class="text-2xl font-bold text-slate-800">€{{ item.cost.toLocaleString() }}</p>
          <div class="mt-2 text-xs text-slate-500">
            {{ getPercentage(item.cost) }}% of total
          </div>
        </div>
      </div>
      
      <div class="bg-gradient-to-r from-blue-600 to-indigo-600 rounded-xl p-6 text-white text-center">
        <p class="text-lg mb-2">Total Trip Cost Per Person</p>
        <p class="text-5xl font-bold">€{{ budget.total.toLocaleString() }}</p>
        <p class="text-sm mt-3 opacity-90">Approximately €{{ Math.round(budget.total / 30) }}/day</p>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  budget: {
    type: Object,
    required: true
  }
})

const getPercentage = (cost) => {
  return Math.round((cost / props.budget.total) * 100)
}

const getCategoryIcon = (category) => {
  const icons = {
    'Accommodation': '<svg class="w-12 h-12 mx-auto text-blue-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"></path></svg>',
    'Transportation': '<svg class="w-12 h-12 mx-auto text-green-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7h12m0 0l-4-4m4 4l-4 4m0 6H4m0 0l4 4m-4-4l4-4"></path></svg>',
    'Food & Groceries': '<svg class="w-12 h-12 mx-auto text-orange-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"></path></svg>',
    'Activities & Entrance Fees': '<svg class="w-12 h-12 mx-auto text-purple-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 5v2m0 4v2m0 4v2M5 5a2 2 0 00-2 2v3a2 2 0 110 4v3a2 2 0 002 2h14a2 2 0 002-2v-3a2 2 0 110-4V7a2 2 0 00-2-2H5z"></path></svg>'
  }
  return icons[category] || ''
}
</script>