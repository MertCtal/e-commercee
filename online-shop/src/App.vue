<template> 
  <div>
    <header>
      <div class="cart-item" @click="router.push({name:'CartView'})">
        <p>Sepetteki Ürünler: {{ store.cart.length }}</p>
      </div>
      <Mainmenu />
    </header>
    <main>
      <router-view />
    </main>
  </div>
</template>

<script setup>
import { useRouter } from "vue-router";
import { productStore } from "./stores/products";
import Mainmenu from './components/Mainmenu.vue';

const router = useRouter();
const store = productStore();
</script>

<script>
import { RouterView } from 'vue-router';

export default {
  name: 'App',
  components: {
    Mainmenu,
    RouterView
  }
}
</script>

<style scoped>
.cart-item {
  text-align: end;
  padding: 16px;
  font-weight: bold;
  font-size: 24px;
  cursor: pointer;
}
</style>