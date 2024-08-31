<template>
      <div v-if="product && product.images && product.images.length" class="product-page">
        <h1>{{ product.title }}</h1>
        <p class="price">{{ product.price }} UAH</p>
    
        <div class="image-gallery">
          <div class="main-image">
            <img :src="product.images[0]" alt="Product Image" />
          </div>
          <div class="thumbnails">
            <img
              v-for="(image, index) in product.images"
              :key="index"
              :src="image"
              class="thumbnail"
            />
          </div>
        </div>
    
        <div class="product-info">
          <p>{{ product.description }}</p>
        </div>
    
        <div class="product-actions">
          <button @click="addToCart">Добавить в корзину</button>
          <button @click="buyNow">Купить в один клик</button>
        </div>
      </div>
    
      <div v-else>
        <p>Loading...</p>
      </div>
    </template>
    
    <script setup>
    import { ref, onMounted } from 'vue'
    import router from '@/router'
    import axios from 'axios'
    
    const id = router.currentRoute.value.params.id
    const product = ref(null)
    
    const getProduct = async () => {
      try {
        const { data } = await axios.get(`http://localhost:3000/products/${id}`)
        product.value = data
      } catch (error) {
        console.error('Mahsulotni olishda xato:', error)
      }
    }
    
    onMounted(() => {
      getProduct()
    })
    
    const addToCart = () => {
      alert('Mahsulot savatga qo\'shildi')
    }
    
    const buyNow = () => {
      alert('Mahsulot bir klik bilan sotib olindi')
    }
    </script>
    
    
    <style lang="scss" scoped>
    .product-page {
      padding: 20px;

    }
    
    .price {
      font-size: 24px;
      font-weight: bold;
    }
    
    .image-gallery {
      display: flex;
      flex-direction: column;
      margin-top: 20px;
    }
    
    .main-image img {
      height: auto;
    }
    
    .thumbnails {
      display: flex;
      margin-top: 10px;
    }
    
    .thumbnail {
      width: 50px;
      height: 50px;
      margin-right: 10px;
      cursor: pointer;
    }
    
    .product-actions {
      display: flex;
      gap: 10px;
      margin-top: 20px;
    }
    
    .product-actions button {
      padding: 10px 20px;
      border: none;
      background-color: #000;
      color: #fff;
      cursor: pointer;
    }
    
    .product-actions button:nth-child(2) {
      background-color: #007bff;
    }
    </style>
    