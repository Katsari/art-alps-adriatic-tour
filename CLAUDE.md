# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a travel itinerary visualization web application for a 30-day European trip. The project is currently in the initial planning phase with requirements defined but no implementation yet started.

### Tech Stack Requirements
- **Framework**: Vue.js 3 with Composition API and `<script setup>` syntax
- **Build Tool**: Vite
- **Styling**: Tailwind CSS 4
- **Icons**: Heroicons or similar SVG icon library

## Development Setup Commands

Since the project hasn't been initialized yet, here are the commands to set it up:

```bash
# Initialize Vue 3 project with Vite
npm create vite@latest . -- --template vue

# Install dependencies
npm install

# Install Tailwind CSS 4 and its dependencies
npm install -D tailwindcss@next @tailwindcss/vite autoprefixer

# Initialize Tailwind configuration
npx tailwindcss init -p

# Install icon library (e.g., Heroicons)
npm install @heroicons/vue

# Run development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Architecture

### Component Structure
The application follows a component-based architecture with these main components:

- **App.vue**: Main container component that orchestrates the layout
- **Header.vue**: Displays the trip title
- **BudgetTracker.vue**: Shows budget breakdown and total cost
- **ItineraryDay.vue**: Card component for each day/period of the trip

### Data Architecture
- All itinerary data is stored in `itineraryData.js`
- The data structure includes:
  - `itinerary`: Array of 8 location blocks covering 30 days
  - `budget`: Object with total cost (€1,550) and category breakdown
- Each itinerary item contains: days, title, description, imageUrl, and links (location/accommodation/transport)

### Key Implementation Requirements
1. **Mobile-first responsive design**
2. **Card-based layout** for itinerary items
3. **External links** for maps, accommodation, and transport
4. **Image headers** for each location card
5. **Budget visualization** component
6. **Neutral background** (e.g., slate-100)
7. **Hover effects** on actionable links

## File Structure
```
travel-itinerary/
├── itineraryData.js      # Complete trip data (8 locations, budget info)
├── project-goal.md       # Detailed project specifications
└── src/                  # Vue source files (to be created)
    ├── App.vue
    ├── components/
    │   ├── Header.vue
    │   ├── BudgetTracker.vue
    │   └── ItineraryDay.vue
    └── main.js
```

## Important Notes
- The project uses placeholder images from Pexels
- All external links in `itineraryData.js` are pre-configured for specific locations
- The budget is calculated per person in Euros (€)
- The trip covers: Italy (Venice, Florence), Croatia (Zagreb), Slovenia (Ljubljana), and Switzerland (Alps)