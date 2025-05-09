<template>
    <div v-if="product" class="border  rounded shadow bg-white relative p-4">
        <h3 class="font-bold">{{ product.title }}</h3>
        <img :src="product.image" alt="" class="h-32 object-contain my-2" />
        <p class="text-sm mb-2">${{ product.price }}</p>

        <div class="flex justify-between items-center">
            <button @click="$emit('see-details', product.id)" class="text-blue-500">See Details</button>
            <div class="flex space-x-2">
                <svg @click="$emit('onEdited', product.id)" xmlns="http://www.w3.org/2000/svg"
                    class="h-5 w-5 cursor-pointer text-green-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                        d="M15.232 5.232l3.536 3.536M9 11l3.536-3.536m0 0L15.232 5.232m-6.768 6.768L5 19l5.768-1.232z" />
                </svg>
                <div @click="$emit('onDeleted', product.id)"
                    class="bg-green-500 px-4 py-1 rounded-xl cursor-pointer select-none">
                    Delete
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { onMounted } from 'vue';
defineProps(['product'])

const { date: product, pending, error } = await useFetch('https://fakestoreapi.com/products')

onMounted(() => {
    product
})


const emit = defineEmits(['onDeleted', 'onEdited', 'see-details'])

// const addTwoNumbers = (a, b, c, d) => {
//     // console.log("Product deleted: ", productId)
//     // emit('onDeleted')
//     return console.log(a + b + c + d)

// }
// const handleonEdit = (productId) => {
//     console.log("Product Edited:", productId)
//     emit('onEdited')
// }

</script>