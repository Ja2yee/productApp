<template>
    <div class="w-64 h-screen bg-gray-800 text-white p-4">
        <h2 class="text-xl font-bold mb-4">Sidebar</h2>
        <ul>
            <li>
                <NuxtLink to="/user/products" class="block py-2">User Products</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/" class="block py-2">Admin Products</NuxtLink>
            </li>
            <li>
                <button @click="goToPage">Life Cycle</button>
            </li>
        </ul>
        <div>
            <button @click="setRouterData">PRINT</button>
        </div>
    </div>
</template>

<script setup>
import { useRouter } from 'vue-router'
import { useRoute } from 'vue-router'

const router = useRouter();
const route = useRoute();

const setRouterData = async () => {
    var name = route.query.name;
    var age = route.query.age;
    console.log("NAME: ", name);
    console.log("AGE: ", age);

    await router.push({
        path: "user",
        query: {
            name: 'asim munir',
            age: 27
        }
    })

    var name = route.query.name;
    var age = route.query.age;
    console.log("NAME: ", name);
    console.log("AGE: ", age);
}
const goToPage = () => {
    navigateTo('/lifecycle')
}



</script>
