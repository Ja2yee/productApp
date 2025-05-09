<template>
    <div class="bg-slate-200 flex flex-col min-h-screen items-center justify-center">
        <h1 class="text-xl ">Add Product</h1>
        <form @submit.prevent="submit" class="flex flex-col ">
            <input v-model="title" placeholder="Title" :required="true"
                class="w-[800px] h-10 border-black border-solid rounded-lg  mb-2 shadow-lg " />
            <input v-model="price" placeholder="Price" type="number" :required="true"
                class="w-[800px] h-10 border-black border-solid rounded-lg  mb-2 shadow-lg " />
            <input v-model="image" placeholder="Image URL" :required="true"
                class="w-[800px] h-10 border-black border-solid rounded-lg  mb-2  shadow-lg" />
            <textarea v-model="description" placeholder="Description" :required="true"
                class="w-[800px] h-10 border-black border-solid rounded-lg  mb-2 shadow-lg " />
            <input v-model="category" placeholder="Category" :required="true"
                class="w-[800px] h-10 border-black border-solid rounded-lg  mb-2 shadow-lg " />
            <button type="submit">Add</button>
        </form>
    </div>
</template>
<script setup>
const title = ref('')
const price = ref('')
const description = ref('')
const image = ref('')
const category = ref('')

const submit = async () => {
    try {
        const product = await $fetch('https://fakestoreapi.com/products', {
            method: 'POST',
            body: {
                title: null,
                price: null,
                description: null,
                image: null,
                category: null,
            },
        })
        alert('Product added: ' + product.id)
        navigateTo('/user/products')
    } catch (error) {
        alert('Error adding product')
        console.error(error)
    }
}
</script>