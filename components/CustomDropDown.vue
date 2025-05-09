<template>
    <div>
        <div @click="isDropDownVisible = true"
            class=" flex border border-gray-300 hover:cursor-pointer rounded p-2 w-auto">
            {{ name }}
            <svg width="30px" height="30px" viewBox="-6.24 -6.24 36.48 36.48" fill="none"
                xmlns="http://www.w3.org/2000/svg">
                >
                <path fill-rule="evenodd" clip-rule="evenodd"
                    d="M12.7071 14.7071C12.3166 15.0976 11.6834 15.0976 11.2929 14.7071L6.29289 9.70711C5.90237 9.31658 5.90237 8.68342 6.29289 8.29289C6.68342 7.90237 7.31658 7.90237 7.70711 8.29289L12 12.5858L16.2929 8.29289C16.6834 7.90237 17.3166 7.90237 17.7071 8.29289C18.0976 8.68342 18.0976 9.31658 17.7071 9.70711L12.7071 14.7071Z"
                    fill="#000000"></path>
            </svg>
        </div>
        <div v-if="isDropDownVisible">

            <div v-for="item, index in countries" :key="index" :value="item" @click="toggleOption(item)"
                class="flex border border-gray-300 rounded p-2 w-auto hover: cursor-pointer">
                {{ item }}

            </div>
        </div>
    </div>


</template>

<script setup>


const props = defineProps({
    countryName: '',
    countries: {
        type: Array,
        required: true
    }

})

const isDropDownVisible = ref(false)
const dropDownIcon = ref(true)


const name = ref(props.countryName)

const toggleOption = (countries) => {
    name.value = countries
    isDropDownVisible.value = false
    dropDownIcon = false
}

</script>


<style></style>