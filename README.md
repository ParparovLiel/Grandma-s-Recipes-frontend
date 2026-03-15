[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/b8J_V0Lj)
🍽️ Grandma’s Recipes — Client Application
Project Overview

Grandma’s Recipes is a full-stack web application that allows users to explore, manage, and organize recipes from multiple sources through a modern web interface.

The system combines:

• External recipes retrieved from the Spoonacular API
• Personal recipes created by users
• Shared family recipes

This repository contains the client-side application, built with Vue.js, responsible for rendering the UI, handling user interactions, and communicating with the backend REST API.

The frontend dynamically displays recipe data, supports authenticated user actions, and provides a modular and responsive user experience.

👥 Team Members

Lidor Mashiach — 209280098
Liel Parparov — 211937354
Noa Shvets — 322548603

🏗 System Architecture

The system follows a client–server architecture.

Frontend (Vue.js)
        │
        │ HTTP Requests (Axios)
        ▼
Backend REST API (Node.js + Express)
        │
        │ SQL Queries
        ▼
MySQL Database
        │
        │ External API
        ▼
Spoonacular Recipe API
Frontend Responsibilities

• Rendering the user interface
• Handling client-side routing
• Managing UI state
• Sending API requests to the backend
• Dynamically rendering recipe data

Backend Responsibilities

• Authentication and session management
• Database access and persistence
• Business logic and API orchestration
• Integration with external recipe services

✨ Main Features

The application supports a range of features designed for recipe exploration and management.

🔎 Recipe Search

Users can search for recipes using filters such as cuisine, diet, and intolerances.

📖 Recipe View

Detailed recipe pages displaying ingredients, preparation steps, and additional metadata.

⭐ Favorite Recipes

Users can save and manage favorite recipes.

👤 Personal Recipes

Users can create and manage their own recipes.

👨‍👩‍👧‍👦 Family Recipes

Shared recipes accessible by family members.

🍽 Weekly Meal Plan

Plan meals for the week using selected recipes.

👁 Recently Viewed Recipes

Tracks recipes previously viewed by the user.

🛠 Technology Stack
Frontend

Vue.js 3
Vue Router
Axios
Bootstrap 5
BootstrapVue3
Vue Toastification

Backend

Node.js
Express.js
MySQL
REST API

External Integration

Spoonacular Recipe API

📁 Project Structure
src
│
├── components
│   ├── RecipePreview.vue
│   ├── RecipePreviewList.vue
│   ├── SearchForm.vue
│   ├── SearchResults.vue
│   ├── CreateRecipeForm.vue
│   └── MealSection.vue
│
├── pages
│   ├── MainPage.vue
│   ├── LoginPage.vue
│   ├── RegisterPage.vue
│   ├── SearchPage.vue
│   ├── RecipeViewPage.vue
│   ├── FavoriteRecipesPage.vue
│   ├── MyRecipesPage.vue
│   ├── FamilyRecipesPage.vue
│   ├── MealPlanPage.vue
│   └── NotFoundPage.vue
│
├── router
│   └── index.js
│
├── store.js
├── constants.js
├── main.js
└── App.vue

The frontend follows a component-based architecture, separating reusable UI components from full application views.

🔗 Backend Integration

The frontend communicates with the backend using Axios for REST API requests.

During local development, the backend server runs at:

http://localhost:3000

The backend handles authentication, database operations, and integration with the Spoonacular API.

🧱 Local Setup
Requirements

Node.js 18.x
npm

A running instance of the backend server.

Installation

Clone the repository:

git clone https://github.com/ParparovLiel/Grandma-s-Recipes-frontend.git

Install dependencies:

npm install

Start the development server:

npm run serve

The application will run at:

http://localhost:8080

🚀 Future Improvements

Possible extensions include:

• improved mobile responsiveness
• advanced recipe filtering
• user profile management
• performance optimizations
