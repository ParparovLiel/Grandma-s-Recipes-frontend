<template>
  <div class="meal-plan-page">
    <header class="meal-header">
      <h1>Hey {{ currentUser }}</h1>
      <p>New week new meal plan. Create your weekly plans!</p>
      <div class="week-navigation">
        <button @click="prevWeek">&larr;</button>
        <span>Week {{ currentWeek }}</span>
        <button @click="nextWeek">&rarr;</button>
      </div>
    </header>

    <div class="days-selector">
      <div
        v-for="day in daysOfWeek"
        :key="day"
        :class="['day-tab', { active: selectedDay === day }]"
        @click="selectedDay = day"
      >
        {{ day }}
      </div>
    </div>

    <div class="meals-section">
      <MealSection
        v-for="meal in mealTypes"
        :key="meal"
        :mealType="meal"
        :mealData="getMealForDayAndType(selectedDay, meal)"
      />
    </div>
  </div>
</template>

<script>
import MealSection from "@/components/MealSection.vue";
import axios from "axios";

export default {
  components: { MealSection },
  data() {
    return {
      currentUser: "User", // later bind from store/session
      currentWeek: 25,
      selectedDay: "Monday",
      daysOfWeek: ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"],
      mealTypes: ["Breakfast", "Lunch", "Dinner"],
      mealPlan: {},
    };
  },
  created() {
    this.fetchMealPlan();
  },
  methods: {
    async fetchMealPlan() {
      try {
        const res = await axios.get("/api/user/meal-plan", { withCredentials: true });
        this.organizeMealPlan(res.data);
      } catch (err) {
        console.error("Failed to fetch meal plan", err);
      }
    },
    organizeMealPlan(entries) {
      const plan = {};
      for (const entry of entries) {
        if (!plan[entry.day]) plan[entry.day] = {};
        plan[entry.day][entry.mealType] = entry;
      }
      this.mealPlan = plan;
    },
    getMealForDayAndType(day, type) {
      return this.mealPlan[day]?.[type] || null;
    },
    nextWeek() {
      this.currentWeek++;
    },
    prevWeek() {
      if (this.currentWeek > 1) this.currentWeek--;
    },
  },
};
</script>

<style scoped>
.meal-plan-page {
  padding: 2rem;
  font-family: 'Segoe UI', sans-serif;
}

.meal-header {
  text-align: left;
  margin-bottom: 2rem;
}

.week-navigation {
  display: flex;
  gap: 1rem;
  align-items: center;
}

.days-selector {
  display: flex;
  justify-content: space-between;
  margin: 1rem 0;
}

.day-tab {
  cursor: pointer;
  padding: 0.5rem 1rem;
  border-radius: 5px;
  border: 1px solid #ccc;
  transition: 0.2s;
}

.day-tab.active {
  background-color: #ddeeff;
  font-weight: bold;
}

.meals-section {
  display: flex;
  justify-content: space-between;
  gap: 1rem;
  margin-top: 1rem;
}
</style>
