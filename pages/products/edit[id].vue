<template>
    <div class="p-4">
        <div v-if="pending">⏳ Loading...</div>
        <div v-if="error">❌ Error: {{ error.message }}</div>

        <div v-if="product">
            <h2 class="text-2xl font-bold mb-2">{{ product.title }}</h2>
            <img :src="product.image" class="h-64 object-contain" />
            <p class="mt-2">{{ product.description }}</p>

            <input v-model="title" class="border p-2 rounded w-full" />
            <textarea v-model="discription" class="border p-2 rounded w-full mt-2" />
            <button @click="updateData" class="bg-blue-500 text-white px-4 py-2 mt-2 rounded">Save</button>
        </div>
    </div>
</template>

<script setup>
import { toast } from 'vue3-toastify';



const { data: product, pending, error } = await useFetch('https://fakestoreapi.com/products/1')

const updateData = async () => {
    try {
        const response = await $fetch(`https://fakestoreapi.com/products/1`, {
            method: 'PUT',
            body: {
                title: null,
                description: null,
            },
        })
        toast.success('Data updated successfully:')
        // navigateTo('/user/products')
        router.push({ path: router.path, query: { param1: 'param1', param2: 'param2' } })
    } catch (err) {
        console.error('Error updating data:', err)
    }

}
</script>