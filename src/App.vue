<template>
  <div id="app">
    <header>
      <h1>OVERTONIGHT OFFICIAL MERCH</h1>
      <p>COLLECTION 2026</p>

      <nav class="nav-bar">
        <button 
          :class="{ active: currentTab === 'home' }" 
          @click="currentTab = 'home'"
        >
          HOME
        </button>
        <button 
          :class="{ active: currentTab === 'catalog' }" 
          @click="currentTab = 'catalog'"
        >
          CATALOG
        </button>
        <button 
          :class="{ active: currentTab === 'contact' }" 
          @click="currentTab = 'contact'"
        >
          CONTACT
        </button>
      </nav>
    </header>

    <main>
      <LandingPage 
        v-if="currentTab === 'home'" 
        @explore="currentTab = 'catalog'" 
      />

      <section v-else-if="currentTab === 'catalog'" class="catalog-grid">
        <ProductCard
          v-for="item in products"
          :key="item.id"
          :product="item"
          @buy="handleBuy"
        />
      </section>

      <ContactPage v-else-if="currentTab === 'contact'" />
    </main>

    <footer>
      <p>&copy; 2026 OFFICIAL MERCHANDISE STORE</p>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ProductCard from './components/ProductCard.vue'
import ContactPage from './components/ContactPage.vue'
import LandingPage from './components/LandingPage.vue'

const currentTab = ref('home')

const products = ref([
  {
    id: 1,
    name: 'cool shirt',
    price: 693000,
    image: '/images/shirt.jpg'
  },
  {
    id: 2,
    name: 'cool hoodie',
    price: 693000,
    image: '/images/hoodie.jpg'
  },
  {
    id: 3,
    name: 'cool black hat (black)',
    price: 365000,
    image: '/images/hat.jpg'
  },
  {
    id: 4,
    name: 'cool pink hat',
    price: 1185000,
    image: '/images/hat.jpg'
  },
  {
    id: 5,
    name: 'cool black hat (white)',
    price: 365000,
    image: '/images/hat.webp'
  },
  {
    id: 6,
    name: 'sticker pack vinyl',
    price: 50000,
    image: '/images/hat.jpg'
  }
])

const handleBuy = (productName) => {
  alert(`Added to cart: ${productName}`)
}
</script>

<style>

.nav-bar {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  margin-top: 1.5rem;
}

.nav-bar button {
  background: transparent;
  border: none;
  color: #777777;
  font-size: 0.85rem;
  letter-spacing: 2px;
  cursor: pointer;
  padding-bottom: 4px;
  transition: color 0.2s ease, border-bottom 0.2s ease;
}

.nav-bar button.active,
.nav-bar button:hover {
  color: #ffffff;
  border-bottom: 2px solid #ffffff;
}
</style>