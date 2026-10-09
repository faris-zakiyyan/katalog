<template>
  <div class="landing-container">
    <div class="hero-section">
      <p class="hero-subtitle">NEW DROP 2026</p>
      <h2 class="hero-title">OVERTONIGHT COLLECTION</h2>
      <p class="hero-description">
        Exclusive streetwear merch designed for the bold. Limited pieces available.
      </p>
      <button class="btn-hero" @click="$emit('explore')">
        EXPLORE COLLECTION
      </button>
    </div>

    <!-- Banner Feature / Highlights -->
    <div class="features-grid">
      <div class="feature-item">
        <h4>HIGH QUALITY FABRIC</h4>
        <p>100% Premium Heavyweight Cotton</p>
      </div>
      <div class="feature-item">
        <h4>LIMITED EDITION</h4>
        <p>No Restocks Once Sold Out</p>
      </div>
      <div class="feature-item">
        <h4>EXPRESS SHIPPING</h4>
        <p>Worldwide Fast Delivery</p>
      </div>
    </div>
  </div>
</template>

<script setup>
defineEmits(['explore'])
</script>

<style scoped>
.landing-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.hero-section {
  padding: 4rem 1rem 5rem;
  max-width: 800px;
}

.hero-subtitle {
  color: #888888;
  font-size: 0.85rem;
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-bottom: 1rem;
}

.hero-title {
  font-size: 2.8rem;
  font-weight: 800;
  letter-spacing: 2px;
  line-height: 1.1;
  margin-bottom: 1.5rem;
  text-transform: uppercase;
}

.hero-description {
  color: #aaaaaa;
  font-size: 1rem;
  line-height: 1.6;
  max-width: 550px;
  margin: 0 auto 2.5rem;
}

.btn-hero {
  padding: 1rem 2.5rem;
  background-color: #ffffff;
  color: #000000;
  border: none;
  font-weight: 800;
  font-size: 0.85rem;
  letter-spacing: 2px;
  cursor: pointer;
  text-transform: uppercase;
  transition: transform 0.2s ease, background-color 0.2s ease;
}

.btn-hero:hover {
  background-color: #cccccc;
  transform: translateY(-2px);
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 2rem;
  width: 100%;
  max-width: 1000px;
  margin-top: 2rem;
  padding-top: 3rem;
  border-top: 1px solid #222222;
}

.feature-item h4 {
  font-size: 0.9rem;
  letter-spacing: 1.5px;
  margin-bottom: 0.5rem;
  color: #ffffff;
}

.feature-item p {
  font-size: 0.8rem;
  color: #777777;
}
</style>