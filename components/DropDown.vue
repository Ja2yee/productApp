<template>
    <div>
        <select class="border border-gray-300 rounded p-2 w-60" v-model="selectedValue">
            <option value="">{{ name }}</option>
            <option v-for="item, index in countries" :key="index" :value="item">
                {{ item }}
            </option>
        </select>
    </div>
</template>

<script setup>
const selectedValue = ref('')
const props = defineProps({
    name: '',
    countries: {
        type: Array,
        required: true
    }
})


</script>