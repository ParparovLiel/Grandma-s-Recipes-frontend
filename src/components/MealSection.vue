<template>
  <div class="meal-section">
    <h3 class="meal-title">{{ mealType }}</h3>

    <div v-if="mealData" class="meal-card">
      <img :src="mealData.image" alt="Meal Image" class="meal-image" />
      <div class="meal-info">
        <p class="meal-name">{{ mealData.title }}</p>
        <div class="meal-meta">
          <span>{{ mealData.readyInMinutes }} mins</span>
          <span class="difficulty">Super Easy</span>
        </div>
        <button class="add-btn">ADD</button>
      </div>
    </div>

    <div v-else class="empty-meal">
      <p>No meal planned</p>
      <button class="add-btn">ADD</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    mealType: String,
    mealData: Object,
  },
};
</script>

<style scoped>
.meal-section {
  flex: 1;
  border-radius: 12px;
  background-color: #f8f9fb;
  padding: 1rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
  text-align: center;
}

.meal-title {
  font-size: 1.2rem;
  margin-bottom: 1rem;
  color: #3a3a3a;
  text-decoration: underline teal;
}

.meal-card {
  background-color: white;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.meal-image {
  width: 100%;
  height: 120px;
  object-fit: cover;
}

.meal-info {
  padding: 0.75rem;
}

.meal-name {
  font-weight: bold;
  font-size: 1rem;
  margin-bottom: 0.5rem;
  color: #222;
}

.meal-meta {
  font-size: 0.85rem;
  color: #666;
  margin-bottom: 1rem;
  display: flex;
  justify-content: space-between;
  padding: 0 0.5rem;
}

.add-btn {
  background-color: #00b894;
  border: none;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 6px;
  font-weight: 600;
  cursor: pointer;
  transition: 0.2s ease;
}

.add-btn:hover {
  background-color: #019875;
}

.empty-meal {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  color: #999;
}
</style>
