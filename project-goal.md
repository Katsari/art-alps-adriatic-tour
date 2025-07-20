**Project Goal:**
Create a beautiful, simple, and responsive single-page web application to visualize a 30-day European travel itinerary. The application should be built with **Vue.js 3 (using the Composition API and `<script setup>` syntax)** and styled with **Tailwind CSS 4**. The app will display the trip day-by-day, including pictures, external links for booking and maps, and a summary of the budget.

**Tech Stack:**
*   **Framework:** Vue.js 3 (Vite as the build tool)
*   **Styling:** Tailwind CSS 4
*   **Icons:** An icon library like `heroicons` (or another free SVG icon library compatible with Vue)

**Key Features:**
1.  **Responsive Design:** The layout must be mobile-first and look great on all screen sizes, from phones to desktops.
2.  **Header Section:** A clean header with the title of the trip, e.g., "30-Day European Adventure: Italy, Croatia, Slovenia & Switzerland."
3.  **Budget Analysis Component:** A visually appealing section near the top that breaks down the estimated budget per person. It should display categories (Accommodation, Transport, Food, Activities) and their corresponding costs (€), along with the total trip cost. A simple table or styled divs would work well.
4.  **Day-by-Day Itinerary Feed:**
    *   The main content of the app should be a feed of "cards," with each card representing one day or a multi-day block of the itinerary.
    *   Each card should be clearly separated and visually distinct.
    *   The background of the page should be a neutral, light color (e.g., `slate-100`).

**Detailed Card Component (`ItineraryDay.vue`):**
Each card in the itinerary feed must contain the following elements:
*   **Image Header:** A high-quality, relevant image at the top of the card representing the location (e.g., Venice canals, Plitvice waterfalls, Lake Bled). Use placeholder images from a service like Pexels or Unsplash.
*   **Day and Title:** A prominent heading indicating the day(s) and the location/focus (e.g., "Days 1-3: Venice & The Islands").
*   **Description:** A short paragraph describing the plan for that day/period.
*   **Actionable Links:** A row of icon-based links for:
    *   **Location:** A map pin icon linking to a specific Google Maps URL.
    *   **Accommodation:** A bed icon linking to a pre-filled Booking.com or Hostelworld search URL.
    *   **Transportation:** A bus/train icon linking to a relevant transport provider's website (e.g., Flixbus, Trainline).
    *   Style these links with a hover effect for better user experience.

**Data Structure:**
The entire itinerary should be stored locally in a single JavaScript/TypeScript file (e.g., `itineraryData.js`). This file will export an array of objects. Each object represents a card and should follow this structure:

```javascript
export const itinerary = [
  {
    id: 1,
    days: "Days 1-3",
    title: "Venice & The Islands, Italy",
    description: "Arrive in Venice, explore the canals, and take a Vaporetto to the colorful islands of Murano and Burano before heading to Croatia.",
    imageUrl: "https://images.pexels.com/photos/219014/pexels-photo-219014.jpeg", // Example URL
    links: {
      location: "https://www.google.com/maps/place/Venice,+Metropolitan+City+of+Venice,+Italy/",
      accommodation: "https://www.hostelworld.com/search?search_keywords=Venice%20Mestre,%20Italy",
      transport: "https://www.flixbus.com/"
    }
  },
  // ... more objects for each part of the trip
];

export const budget = {
  total: 1500,
  breakdown: [
    { category: 'Accommodation', cost: 825 },
    { category: 'Transportation', cost: 350 },
    { category: 'Food & Local Transport', cost: 225 },
    { category: 'Activities & Buffer', cost: 100 }
  ]
};
```
(Please use the full 30-day itinerary provided (itineraryData.js) to populate this data file.)

**Component Breakdown:**
Please structure the Vue application into the following components:

* App.vue (Main Component):
Imports and renders the Header, BudgetTracker, and ItineraryDay components.
Contains the main layout container (e.g., a div with flex column layout).
Loops through the itineraryData using v-for to render a ItineraryDay card for each item.

* Header.vue (Presentational Component):
Displays the main title of the trip.

* BudgetTracker.vue (Presentational Component):
Receives the budget data as a prop.
Displays the budget breakdown in a clean, easy-to-read format.

* ItineraryDay.vue (Presentational Component):
Receives a single itinerary object as a prop.
Renders the card structure as described above (image, title, description, links).

**Final Output Request:**
Please provide the complete code for all the .vue components and use the provided itinerary data file (./itineraryData.js). Include the necessary commands to set up a new Vue.js project with Vite and install Tailwind CSS 4, so I can copy, paste, and run the application locally.