<script setup>
import { ref, computed } from 'vue'

// Data produk/item lokal
const products = ref([
  { id: 1, name: 'Overtonight Oversized Hoodie', category: 'Apparel', price: 'Rp 350.000' },
  { id: 2, name: 'Overtonight Heavyweight Graphic Tee', category: 'Apparel', price: 'Rp 180.000' },
  { id: 3, name: 'Overtonight Snapback Cap', category: 'Accessories', price: 'Rp 120.000' },
  { id: 4, name: 'Overtonight Tote Bag', category: 'Accessories', price: 'Rp 90.000' }
])

// State untuk menyimpan keyword pencarian
const searchQuery = ref('')

// Computed property untuk memfilter produk secara otomatis setiap kali searchQuery berubah
const filteredProducts = computed(() => {
  const query = searchQuery.value.toLowerCase().trim()
  
  if (!query) return products.value

  return products.value.filter(product => {
    return (
      product.name.toLowerCase().includes(query) ||
      product.category.toLowerCase().includes(query)
    )
  })
})
</script>

<template>
  <div class="search-container">
    <h2>Katalog Merch</h2>
    
    <!-- Input Pencarian -->
    <div class="input-group">
      <input
        v-model="searchQuery"
        type="text"
        placeholder="Cari produk atau kategori..."
        class="search-input"
      />
      <button v-if="searchQuery" @click="searchQuery = ''" class="clear-btn">
        Reset
      </button>
    </div>

    <!-- Daftar Hasil -->
    <div class="product-list">
      <div 
        v-for="item in filteredProducts" 
        :key="item.id" 
        class="product-card"
      >
        <h3>{{ item.name }}</h3>
        <p class="category">{{ item.category }}</p>
        <p class="price">{{ item.price }}</p>
      </div>

      <!-- Tampilan jika data tidak ditemukan -->
      <div v-if="filteredProducts.length === 0" class="no-results">
        <p>Produk dengan kata kunci "<strong>{{ searchQuery }}</strong>" tidak ditemukan.</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.search-container {
  max-width: 500px;
  margin: 20px auto;
  font-family: Arial, sans-serif;
}

.input-group {
  display: flex;
  gap: 8px;
  margin-bottom: 20px;
}

.search-input {
  width: 100%;
  padding: 10px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.clear-btn {
  padding: 10px 15px;
  background-color: #f44336;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.product-card {
  border: 1px solid #e0e0e0;
  padding: 12px;
  border-radius: 6px;
  margin-bottom: 10px;
}

.product-card h3 {
  margin: 0 0 5px 0;
  font-size: 16px;
}

.category {
  color: #666;
  font-size: 12px;
  margin: 0 0 5px 0;
}

.price {
  font-weight: bold;
  color: #111;
  margin: 0;
}

.no-results {
  text-align: center;
  color: #777;
  padding: 20px;
}
</style>