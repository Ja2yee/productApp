<template>
    <div>
        <h2 class="text-xl font-bold mb-4">Admin Products</h2>
        <button>Add Poduct</button>
        <div v-if="product" class="grid grid-cols-1 md:grid-cols-3 gap-4">
            <ProductCard v-for="products in product" :key="product.id" :product="product" @onDeleted="openDeleteModal"
                @see-details="goToDetails" @edit="goToEdit" />
        </div>
        <DeleteModal v-if="showModal" @close="showModal = false" @confirm="deleteProduct" />
    </div>
</template>

<script setup>

definePageMeta({
    layout: 'admin'
})

const products = ref([])
const showModal = ref(false)
const productToDelete = ref(null)
const router = useRouter()


const { date: product, pending, error } = await useFetch('https://fakestoreapi.com/products')

const openDeleteModal = (id) => {
    productToDelete.value = id
    showModal.value = true
}

const deleteProduct = () => {
    products.value = products.value.filter(p => p.id !== productToDelete.value)
    showModal.value = false
}

const goToDetails = (id) => {
    router.push(`/product/${id}`)
}

const goToEdit = (id) => {
    router.push(`/product/${id}?edit=true`)
}

onMounted(products)
</script>