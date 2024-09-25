<script setup>
import { onMounted, ref } from 'vue';
import axios from "axios"

const products = ref([])

  const fetchAllProducts = async () => {
    const response = await axios.get("https://fakestoreapi.com/products")
    products.value = response.data
  }

  onMounted(async() => await fetchAllProducts())
</script>

<template>
  <h1>Welcome to the fake store!</h1>
  <div class="grid grid-cols-4">
    <article v-for="product in products" :key="product.id">
      <img :src="product.image">
      <h4>{{ product.title }}</h4>
    </article>
  </div>
</template>

