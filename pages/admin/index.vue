<!-- <template>
    <div class="p-10">
        <h1 class="text-2xl font-bold mb-4">Admin Panel</h1>
        <div class="grid grid-cols-2 gap-6">
            <div v-for="product in products" :key="product.id" class="p-4 bg-white shadow relative">
                <img :src="product.image" class="h-40 mx-auto" />
                <h2>{{ product.title }}</h2>
                <p>${{ product.price }}</p>
                <div class="absolute top-4 right-4 flex gap-2">
                    <button class="bg-blue-400 text-white px-2 py-1 rounded">Edit</button>
                    <button @click="removeProduct(product.id)"
                        class="bg-red-500 text-white px-2 py-1 rounded">Delete</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { useStore } from 'vuex'
import { onMounted, computed } from 'vue'

const store = useStore()

const products = computed(() => store.getters['products/allProducts'])

onMounted(() => {
    store.dispatch('products/fetchProducts')
})

const removeProduct = (id) => {
    store.dispatch('products/deleteProduct', id)
}
</script> -->

<template>
    <div>

    </div>
</template>

<script setup>
definePageMeta({
    layout: 'admin'
})
</script>

<style></style>