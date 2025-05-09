<template>
    <div class="flex flex-col justify-center items-center min-h-screen">

        <div v-if="pending">⏳ Loading...</div>
        <div v-if="error">❌ Error: {{ error.message }}</div>

        <div class="flex flex-col item-center  justify-center">

            <h2 class="text-xl font-bold mb-4">User Products</h2>
            <button @click="addProduct" class="rounded shadow-lg bg-gray-500 w-fit">Add new product</button>
            <div v-if="product" class="grid grid-cols-1 md:grid-cols-3 gap-4 mx-4">
                <ProductCard v-for="product in products" :key="product.id" :product="product"
                    @onDeleted="openDeleteModal" @see-details="goToDetails" @onEdited="goToEdit" />
            </div>
            <DeleteModal v-if="showModal" @close="closeModal" @confirm="deleteProduct" />
        </div>
    </div>
</template>

<script setup>
const product = ref([])
const showModal = ref(false)
const productToDelete = ref(null)
const router = useRouter()

const { data: products } = await useFetch(`https://fakestoreapi.com/products/`)


const openDeleteModal = (id) => {
    productToDelete.value = id
    showModal.value = true
}
const closeModal = () => {
    showModal.value = false
}


const deleteProduct = () => {
    products.value = products.value.filter(p => p.id !== productToDelete.value)
    showModal.value = false
}

const goToDetails = (id) => {
    router.push(`/products/${id}`)
}

const goToEdit = (id) => {
    router.push(`/products/edit${id}`)

}
// const onEdited = () => {
//     console.log("Edit ho giya")
//     router.push(`/`)

// }
const addProduct = () => {
    router.push(`/products/add`)
}


</script>