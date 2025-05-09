<template>
    <div class="flex">
        <Sidebar />
        <div class="flex p-4">
            <!-- <DropDown name="selectCounty" , :countries="countryName" v-model="selectCounty" /> -->
        </div>
        <div>
            <!-- <CustomDropDown /> -->
            <CustomDropDown :countryName="selectCounty" , :countries="countryName" />
        </div>
    </div>
</template>

<script setup>
import Sidebar from '~/components/Sidebar.vue'

const selectCounty = ref('Select country from the list')
const countryName = ['pakistan', 'india', 'sirilanka']
</script>
