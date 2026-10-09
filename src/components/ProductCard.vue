<template>
  <div class="product-card">
    <div class="image-wrapper">
      <img :src="product.image" :alt="product.name" class="product-img" />
    </div>
    <div class="product-info">
      <h3 class="product-title">{{ product.name }}</h3>
      <p class="price">Rp {{ product.price.toLocaleString('id-ID') }} IDR</p>
      <button class="btn-buy" @click="$emit('buy', product.name)">
        BUY NOW
      </button>
    </div>
  </div>
</template>

<script setup>
defineProps({
  product: {
    type: Object,
    required: true
  }
})

defineEmits(['buy'])
</script>

<style scoped>
.product-card {
  display: flex;
  flex-direction: column;
  background-color: transparent;
}

.image-wrapper {
  width: 100%;
  aspect-ratio: 1 / 1;
  background-color: #f2f2f2; /* Latar gambar netral seperti produk Ghostland */
  overflow: hidden;
  border-radius: 2px;
}

.product-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.product-card:hover .product-img {
  transform: scale(1.04);
}

.product-info {
  padding-top: 1rem;
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
}

.product-title {
  font-size: 0.95rem;
  font-weight: 500;
  letter-spacing: 0.5px;
  color: #eeeeee;
  text-transform: lowercase;
}

.price {
  font-size: 0.85rem;
  color: #aaaaaa;
}

.btn-buy {
  margin-top: 0.5rem;
  padding: 0.75rem;
  background-color: #ffffff;
  color: #000000;
  border: none;
  font-weight: 700;
  font-size: 0.75rem;
  letter-spacing: 1.5px;
  cursor: pointer;
  text-transform: uppercase;
  transition: background-color 0.2s ease, color 0.2s ease;
}

.btn-buy:hover {
  background-color: #cccccc;
}
</style>