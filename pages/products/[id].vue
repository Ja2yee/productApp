<template>
    <div v-if="product" class="border  rounded shadow bg-white relative p-4">
        <h3 class="font-bold">{{ product.title }}</h3>
        <img :src="product.image" alt="" class="h-32 object-contain my-2" />
        <p class="text-sm mb-2">${{ product.price }}</p>
    </div>
</template>

<script setup>

const { data: product, pending, error } = await useFetch('https://fakestoreapi.com/products')
console.log("erros:   ", error)
console.log("erros:   ", product)
if (!product.value) {
    throw createError({
        statusCode: 404,
        statusMessage: 'product not found'
    })
}
onMounted(() => {
    product
})
</script>