<template>
    <div class="fixed inset-0 flex items-center justify-center">
        <div class="bg-white p-6 rounded shadow-lg">
            <p class="mb-4">Are you sure you want to delete this product?</p>
            <div class="flex justify-end space-x-2">
                <button @click="$emit('close')" class="px-4 py-2 bg-gray-300 rounded">Cancel</button>
                <button @click="$emit('confirm')" class="px-4 py-2 bg-red-500 text-white rounded">Delete</button>
            </div>
        </div>
    </div>
</template>