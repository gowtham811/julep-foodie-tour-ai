# 🧠 AI Agent Description – Foodie Tour Planner

This document outlines the structure, logic, and flow of the AI agent created using the [Julep](https://julep.ai) dashboard to generate a personalized foodie tour for cities like Hyderabad, Bangalore, and Chennai.

---

## 🗂️ Overview

- **Platform**: Julep Dashboard (no-code, visual workflow)
- **APIs Used**:
  - **OpenWeather API**: To retrieve real-time weather conditions for each city.
  - **APIIP API**: To optionally determine the user’s current location based on IP.
- **Goal**: Create an AI agent that generates city-specific foodie itineraries based on weather and cultural cuisine.

---

## 🔁 Agent Workflow (High-Level Steps)

1. **User Input**  
   - Prompt: `Plan a foodie tour for the cities: Hyderabad, Bangalore, Chennai.`
   - The agent accepts city names either directly from the user input or via variable injection in Julep.

2. **Weather Tool (OpenWeather API)**  
   - Fetches current weather data for each city in the tour.
   - Configured with API key via `{{env.OPENWEATHER_API_KEY}}`.

3. **Location Tool (APIIP)** (Optional Step)  
   - Determines user’s current city based on their IP.
   - Used to personalize or suggest a starting point if not explicitly provided.

4. **Foodie Tour Generation (LLM or Planner Step)**  
   - Using weather data and city name, the agent:
     - Highlights iconic dishes of the city.
     - Plans a food itinerary for breakfast, lunch, and dinner.
     - Tailors dining experiences to weather (e.g., indoor dining for hot cities, outdoor for pleasant ones).
   - The plan includes real restaurant recommendations.

5. **Output Response**  
   - A well-formatted, user-friendly response listing dishes and restaurants, one city at a time.

---

## 🧱 Agent Configuration in Julep Dashboard

### Step 1: Input Prompt

Plan a foodie tour for the cities: Hyderabad, Bangalore, Chennai.
### Step 2: Weather API Tool Configuration (OpenWeather)
Input: City name (from user or looped variable)

Output: Current temperature, weather condition

API Key: {{env.OPENWEATHER_API_KEY}}

### Step 3: Location API Tool (APIIP)
Optional: Detect user’s city

Output: City name

API Key: {{env.APIIP_KEY}}

### Step 4: LLM Step – Generate Tour
Prompt Template:

Generate a foodie itinerary for {{city}}. Assume the weather is {{weather}}.
Include:
- 3 Iconic Dishes
- Breakfast Restaurant
- Lunch Restaurant
- Dinner Restaurant

### 🎯 Outcome
The final response from the AI agent is a curated foodie tour with:

Dish highlights

Restaurant names

Adjusted tone for different weather and time of day

All of this is generated dynamically using no-code AI logic via Julep.