<template>
    <div class="flex justify-center items-center h-screen bg-gray-100">
        <div class="bg-white p-6 rounded shadow-md w-full max-w-sm">
            <h2 class="text-2xl font-bold mb-4">Login</h2>
            <form @submit.prevent="loginUser">
                <input v-model="email" placeholder="Email" required="true" class="w-full border p-2 mb-4 rounded" />
                <input v-model="password" type="password" placeholder="Password" required="true"
                    class="w-full border p-2 mb-4 rounded" />
                <button type="submit" class="bg-blue-500 text-white w-full py-2 rounded">Login</button>
                <p class="text-red-500 mt-2" v-if="errorMessage">{{ errorMessage }}</p>
                <p class="text-sm mt-4">Don't have an account?
                    <NuxtLink to="/auth/signup" class="text-blue-600 underline">Register</NuxtLink>
                </p>
            </form>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'
const { loggedIn, user, fetch: refreshSession } = useUserSession()
const email = ref('')
const password = ref('')
const errorMessage = ref('')

const loginUser = async () => {
    const { data, error } = await useFetch('https://staging-ezcrm-api.crm.ezhubspot.com/api/auth/login', {
        method: 'POST',
        body: {
            email: email.value,
            password: password.value
        }
    })

    if (error.value) {
        errorMessage.value = 'invalid username or password'
    }
    else {
        await refreshSession()
        navigateTo('/admin')
    }
}
</script>
<!-- //test -->
<!-- <script setup>
import { ref } from 'vue'
const email = ref('')
const password = ref('')
const { loggedIn, user, fetch: refreshSession } = useUserSession()
// const credentials = reactive({
//     email: email.value,
//     password: password.value,
// })
// async function login() {
//     const { data, erro } = await useFetch('https://staging-ezcrm-api.crm.ezhubspot.com/api/auth/login', {
//         method: 'POST',
//         body: {
//             email: email.value,
//             password: password.value
//         }
//     })

<!-- const loginUser = async () => {
    const { data, error } = await useFetch('https://staging-ezcrm-api.crm.ezhubspot.com/api/auth/login', {
        method: 'POST',
        body: {
            email: email.value,
            password: password.value
        }
    })
        .then(async () => {
            // Refresh the session on client-side and redirect to the home page
            await refreshSession()
            await navigateTo('/user')
        })
        .catch(() => alert('Bad credentials'))
    await navigateTo('/auth/login')
} -->
<!-- </script>

<template>
    <form @submit.prevent="loginUser">
        <input v-model="email" type="email" placeholder="Email" />
        <input v-model="password" type="password" placeholder="Password" />
        <button type="submit">Login</button>

    </form>
</template> -->
