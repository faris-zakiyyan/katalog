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

      <!-- Halaman Catalog + Search -->
      <section v-else-if="currentTab === 'catalog'" class="catalog-section">
        <!-- Input Search Bar -->
        <div class="search-bar">
          <input 
            v-model="searchQuery" 
            type="text" 
            placeholder="Search products..." 
          />
          <button v-if="searchQuery" @click="searchQuery = ''" class="clear-btn">✕</button>
        </div>

        <!-- Grid Produk Hasil Filter -->
        <div class="catalog-grid" v-if="filteredProducts.length > 0">
          <ProductCard
            v-for="item in filteredProducts"
            :key="item.id"
            :product="item"
            @buy="handleBuy"
          />
        </div>

        <!-- Pesan jika produk tidak ditemukan -->
        <div v-else class="no-results">
          <p>No products found matching "{{ searchQuery }}"</p>
        </div>
      </section>

      <ContactPage v-else-if="currentTab === 'contact'" />
    </main>

    <footer>
      <p>&copy; 2026 OFFICIAL MERCHANDISE STORE</p>
    </footer>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import ProductCard from './components/ProductCard.vue'
import ContactPage from './components/ContactPage.vue'
import LandingPage from './components/LandingPage.vue'

const currentTab = ref('home')
const searchQuery = ref('')

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
    image: '/images/hat.webp'
  },
  {
    id: 5,
    name: 'cool black hat (white)',
    price: 365000,
    image: '/images/hat.jpg'
  },
  {
    id: 6,
    name: 'ghostland forever cd',
    price: 500000,
    image: '/images/vinyl.jpg'
  }
])

const filteredProducts = computed(() => {
  const query = searchQuery.value.toLowerCase().trim()
  if (!query) return products.value

  return products.value.filter((item) =>
    item.name.toLowerCase().includes(query)
  )
})

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

.search-bar {
  position: relative;
  max-width: 400px;
  margin: 2rem auto;
  display: flex;
  align-items: center;
}

.search-bar input {
  width: 100%;
  padding: 10px 16px;
  background-color: #111111;
  border: 1px solid #333333;
  color: #ffffff;
  border-radius: 4px;
  font-size: 0.9rem;
  outline: none;
  transition: border-color 0.2s ease;
}

.search-bar input:focus {
  border-color: #ffffff;
}

.clear-btn {
  position: absolute;
  right: 12px;
  background: transparent;
  border: none;
  color: #888888;
  cursor: pointer;
  font-size: 0.9rem;
}

.clear-btn:hover {
  color: #ffffff;
}

.no-results {
  text-align: center;
  color: #777777;
  margin: 3rem 0;
}
</style>