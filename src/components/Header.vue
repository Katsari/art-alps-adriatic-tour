<template>
  <header class="relative py-12 sm:py-16 px-4 overflow-hidden min-h-[300px] sm:min-h-[400px] flex items-center">
    <!-- Background image with subtle zoom animation -->
    <div class="absolute inset-0 -z-10">
      <img 
        src="https://images.pexels.com/photos/10478251/pexels-photo-10478251.jpeg?auto=compress&cs=tinysrgb&w=1920&q=80"
        alt="Lake Bled, Slovenia"
        class="w-full h-full object-cover object-center scale-105 animate-slow-zoom brightness-[0.3] contrast-150 saturate-50"
        loading="eager"
      />
      <div class="absolute inset-0 bg-gradient-to-b from-black/80 via-black/70 to-black/80"></div>
    </div>
    
    <div class="max-w-4xl mx-auto text-center relative z-10 w-full">
      <h1 class="text-2xl sm:text-4xl md:text-5xl lg:text-6xl font-extrabold text-white mb-3 sm:mb-4 drop-shadow-lg leading-tight">
        The Art, Alps & Adriatic Tour
      </h1>
      <p class="text-base sm:text-xl md:text-2xl text-white/90 font-medium drop-shadow-md">
        Italy • Croatia • Slovenia • Switzerland
      </p>
      <div class="mt-4 sm:mt-6 flex flex-wrap justify-center gap-3 sm:gap-6 md:gap-8 text-xs sm:text-sm md:text-base text-white/80">
        <span class="flex items-center gap-1 sm:gap-2">
          <svg class="w-4 h-4 sm:w-5 sm:h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"></path>
          </svg>
          30 Days
        </span>
        <span class="flex items-center gap-1 sm:gap-2">
          <svg class="w-4 h-4 sm:w-5 sm:h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path>
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
          </svg>
          8 Destinations
        </span>
        <span class="flex items-center gap-1 sm:gap-2">
          <svg class="w-4 h-4 sm:w-5 sm:h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
          </svg>
          €1,923/person
        </span>
      </div>
    </div>
  </header>
</template>

<script setup>
</script>