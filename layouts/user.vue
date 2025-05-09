<template>
    <div>
        <Header />
        <div class="flex">
            <Sidebar />
            <div class="flex-1 p-4">
                <slot />
            </div>
        </div>
    </div>
</template>

<script setup>
import Header from '~/components/Header.vue'
</script>