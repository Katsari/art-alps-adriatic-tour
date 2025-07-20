<template>
  <div class="bg-white rounded-xl shadow-lg overflow-hidden mb-4 sm:mb-6 md:mb-8 transition-all duration-300 hover:shadow-xl">
    <div class="p-4 sm:p-6 md:p-8">
      <div class="flex items-center justify-between mb-4">
        <h2 class="text-xl sm:text-2xl font-bold text-slate-800 flex items-center gap-2">
          <svg class="w-5 h-5 sm:w-6 sm:h-6 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 20l-5.447-2.724A1 1 0 013 16.382V5.618a1 1 0 011.447-.894L9 7m0 13l6-3m-6 3V7m6 10l4.553 2.276A1 1 0 0021 18.382V7.618a1 1 0 00-.553-.894L15 4m0 13V4m0 0L9 7"></path>
          </svg>
          The 30-Day Route
        </h2>
        <a 
          href="https://www.google.com/maps/dir/Zagreb,+Croatia/Rovinj,+Croatia/Pula,+Croatia/Ljubljana,+Slovenia/Lake+Bled,+Slovenia/Bolzano,+Italy/Tirano,+Italy/St.+Moritz,+Switzerland/Florence,+Italy/Venice,+Italy"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-flex items-center gap-2 px-3 py-1.5 sm:px-4 sm:py-2 bg-blue-600 text-white text-sm font-medium rounded-lg hover:bg-blue-700 transition-colors"
        >
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"></path>
          </svg>
          <span class="hidden sm:inline">Open in</span> Google Maps
        </a>
      </div>
      
      <div class="mb-4">
        <p class="text-sm text-slate-600">
          <span class="font-medium">Total Distance:</span> ~2,200 km • 
          <span class="font-medium">Countries:</span> Croatia → Slovenia → Italy → Switzerland
        </p>
      </div>

      <!-- Embedded Map -->
      <div class="relative w-full h-[300px] sm:h-[400px] md:h-[500px] rounded-lg overflow-hidden bg-slate-100">
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m76!1m12!1m3!1d5756219.309755097!2d11.492187046875!3d45.74265056534901!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!4m61!3e0!4m5!1s0x4765d692c902cc39%3A0x3a45249628fbc28a!2sZagreb%2C%20Croatia!3m2!1d45.815399!2d15.981919!4m5!1s0x477c3daa64151ff1%3A0x8d37d769b24e61f4!2sRovinj%2C%20Croatia!3m2!1d45.0811661!2d13.638706999999999!4m5!1s0x477cd2de09337b6d%3A0x72324a3a7b4e580d!2sPula%2C%20Croatia!3m2!1d44.8666232!2d13.849579099999999!4m5!1s0x476531f5969886d1%3A0x400f81c823fec20!2sLjubljana%2C%20Slovenia!3m2!1d46.0569465!2d14.5057515!4m5!1s0x477a66a28e51c381%3A0xbe55145a959a6796!2sLake%20Bled%2C%20Slovenia!3m2!1d46.368199399999996!2d14.1038771!4m5!1s0x47831158cb498369%3A0x46619ac09b1d6469!2sBolzano%2C%20Province%20of%20Bolzano%20-%20South%20Tyrol%2C%20Italy!3m2!1d46.498295399999994!2d11.354758099999999!4m5!1s0x4783a53bab832cd1%3A0x966b7e840b9f3ff!2sTirano%2C%20Province%20of%20Sondrio%2C%20Italy!3m2!1d46.2141872!2d10.168917899999999!4m5!1s0x478fafb3640de239%3A0xe21559b1e01e3fec!2sSt.%20Moritz%2C%20Switzerland!3m2!1d46.4907973!2d9.8355079!4m5!1s0x132a5127874a0521%3A0x5861f452e8d29e02!2sFlorence%2C%20Metropolitan%20City%20of%20Florence%2C%20Italy!3m2!1d43.7695604!2d11.2558136!4m5!1s0x477eb1daf1d63d89%3A0x7ba3c6f0bd92102f!2sVenice%2C%20Metropolitan%20City%20of%20Venice%2C%20Italy!3m2!1d45.4408474!2d12.3155151!5e0!3m2!1sen!2sus!4v1737384523456!5m2!1sen!2sus"
          width="100%"
          height="100%"
          style="border:0;"
          allowfullscreen=""
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
          class="absolute inset-0"
        ></iframe>
      </div>

      <!-- Route Summary -->
      <div class="mt-6 grid grid-cols-1 sm:grid-cols-2 gap-4">
        <div class="space-y-2">
          <h3 class="font-semibold text-slate-800">Route Highlights:</h3>
          <ul class="text-sm text-slate-600 space-y-1">
            <li class="flex items-start gap-2">
              <span class="text-blue-600 mt-1">•</span>
              <span><strong>Days 1-6:</strong> Zagreb & Plitvice Lakes</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-blue-600 mt-1">•</span>
              <span><strong>Days 7-10:</strong> Istrian Coast (Rovinj & Pula)</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-blue-600 mt-1">•</span>
              <span><strong>Days 10-14:</strong> Ljubljana & Lake Bled</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-blue-600 mt-1">•</span>
              <span><strong>Days 14-19:</strong> Dolomites (Bolzano)</span>
            </li>
          </ul>
        </div>
        <div class="space-y-2">
          <h3 class="font-semibold text-slate-800">&nbsp;</h3>
          <ul class="text-sm text-slate-600 space-y-1">
            <li class="flex items-start gap-2">
              <span class="text-blue-600 mt-1">•</span>
              <span><strong>Days 20-22:</strong> Tirano & Bernina Express</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-blue-600 mt-1">•</span>
              <span><strong>Days 22-26:</strong> Florence</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-blue-600 mt-1">•</span>
              <span><strong>Days 26-30:</strong> Venice</span>
            </li>
          </ul>
        </div>
      </div>

      <div class="mt-4 p-3 bg-blue-50 rounded-lg">
        <p class="text-xs sm:text-sm text-blue-800">
          <strong>Pro tip:</strong> This optimized route saves ~€200 and 18+ hours of travel time compared to backtracking routes!
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
</script>