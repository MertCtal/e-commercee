<template>
    <div class="products-list">
      <div 
        class="products"
        v-for='product in store.products'
        :key="product.id"
        @click="goToProductPage (product.id)"
      >
        <img :src="product.thumbnail" alt="">
        <h2>Marka: {{ product.brand }}</h2>
        <p>Detay: {{ product.description }}</p>
        <p>Fiyat: ${{ product.price }}</p>
        
      </div>
    </div>
  </template>
  
  <script setup>
  import { onMounted} from 'vue';
  import { productStore } from "@/stores/products";
  import { useRouter } from 'vue-router';
  
  const store = productStore();
  const router = useRouter()

  const goToProductPage = (id) => {
    router.push ({name : 'ProductView' ,params : {id}})

  }
  

 
  onMounted(async () => {
    await store.fetchProductsFromDB();
    
  });
  </script>
  
 
 
 
 <style scoped>
  .products-list {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }
  
  .products {
    flex-basis: 28px;
    margin: 8px;
    padding: 16px;
    box-shadow: 0px 0px 14px 1px #e6e6e6;
    cursor: pointer;
  }
  
  .products-item img {
    width: 10%;
  }
  </style>