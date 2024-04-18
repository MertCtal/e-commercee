<template>
     <button @click="router.push({name: 'Catalog'})"> Ana Menüye Dön</button>
    <div class="product">
        <div class="product-image">
            <img :src="selectedProduct.thumbnail" alt="">
        </div>
        <div class="product-details">
            <p>Marka : {{ selectedProduct.brand }}</p>
            <p>Detay : {{ selectedProduct.description }}</p>
            <h2>Fiyat : ${{ selectedProduct.price }}</h2>
            <button @click="addToCart">Ürünü Ekleyiniz</button>            
        </div>
    </div>
   
</template>

<script>
import { defineComponent, computed } from "vue";
import router from "@/router";
export default defineComponent({
    name: 'ProductDetail' // Bileşen adınızı burada düzeltin
})
</script>

<script setup>
import { computed } from "vue";
import { productStore } from '@/stores/products';
import { useRoute ,useRouter } from 'vue-router';

const store = productStore();
const router = useRouter();
const route = useRoute();

const selectedProduct = computed(() => {
    return store.products.find((item) => item.id === Number(route.params.id)); 
});


const addToCart = () => {
    store.addToCart(selectedProduct.value)
    router.push ({name:'CartView'})
}

</script>



<style scoped>
.product {
    display: flex;
    margin-top: 50px;
}
.product-image {
    margin-right: 24px;
    
}

</style>