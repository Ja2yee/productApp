<template>
    <div class="min-h-screen flex flex-col items-center justify-center bg-gray-100">
        <h1 class="text-3xl font-bold mb-6">Welcome! Choose a page</h1>
        <div class="space-x-4">
            <NuxtLink to="/auth/login" class="bg-blue-500 hover:bg-blue-600 text-white py-2 px-4 rounded">
                Login
            </NuxtLink>
            <NuxtLink to="/auth/signup" class="bg-green-500 hover:bg-green-600 text-white py-2 px-4 rounded">
                Signup
            </NuxtLink>
        </div>
    </div>
</template>