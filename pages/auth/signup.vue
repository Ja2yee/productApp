<template>
    <div class="flex justify-center items-center h-screen bg-gray-100">
        <div class="bg-white p-6 rounded shadow-md w-full max-w-sm">
            <h2 class="text-2xl font-bold mb-4">Register</h2>
            <form @submit.prevent="registerUser">
                <input v-model="fullName" placeholder="Full Name" required="true"
                    class="w-full border p-2 mb-4 rounded" />
                <input v-model="organizationName" placeholder="Organization Name" required="true"
                    class="w-full border p-2 mb-4 rounded" />
                <input v-model="email" placeholder="Email" required="true" class="w-full border p-2 mb-4 rounded" />
                <div class="flex items-center border p-2 mb-4 rounded">
                    <input v-model="countryCode" required="true" class="px-3 bg-gray-100 w-16 text-gray-700" />
                    <input v-model="phoneNumber" type="tel" placeholder="Phone number" required="true"
                        class="flex-1 px-4 outline-none" />
                </div>
                <input v-model="password" type="password" placeholder="Password" required="true"
                    class="w-full border p-2 mb-4 rounded" />
                <button type="submit" class="bg-green-500 text-white w-full py-2 rounded">Register</button>
                <p class="text-sm mt-4">
                    Already have an account?
                    <NuxtLink to="/auth/login" class="text-blue-600 underline">Login</NuxtLink>
                </p>
            </form>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import { toast } from 'vue3-toastify'
import 'vue3-toastify/dist/index.css'

const fullName = ref('')
const email = ref('')
const phoneNumber = ref('')
const password = ref('')
const countryCode = ref('PK-92')
const organizationName = ref('')


const registerUser = async () => {
    const { data, error } = await useFetch('https://staging-ezcrm-api.crm.ezhubspot.com/api/auth/register', {
        method: 'POST',
        body: {
            organizationName: organizationName.value,
            fullName: fullName.value,
            email: email.value,
            countryCode: countryCode.value,
            phoneNumber: phoneNumber.value,
            password: password.value
        }
    })

    if (error.value) {
        console.log("ERROR:    ", error)
        toast.error('Registration failed!')
    }
    else {
        toast.success('Registration successful!')
        setTimeout(() => navigateTo('/auth/login'), 2000)
    }
}
</script>