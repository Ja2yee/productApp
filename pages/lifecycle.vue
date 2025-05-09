<!-- <script setup>
import { ref, onBeforeUpdate, onUpdated } from 'vue'

const message = ref('')
let textareaRef = null

// Reset height before update
onBeforeUpdate(() => {
    if (textareaRef) {
        textareaRef.style.height = 'auto'
    }
})

// Resize after DOM is updated
onUpdated(() => {
    if (textareaRef) {
        textareaRef.style.height = textareaRef.scrollHeight + 'px'
    }
})
</script>

<template>
    <div class="p-4">
        <label class="block mb-2">Type Message:</label>
        <textarea ref="textareaRef" v-model="message" rows="1" class="w-full border p-2 resize-none overflow-hidden"
            placeholder="Start typing..." />
    </div>
</template> -->
<!-- <script setup>
import { ref, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted } from 'vue'

// Reactive message and background color state
const message = ref('')
const bgColor = ref('lightblue')  // Initially, background color is lightblue

let timer = null

// 🔹 onBeforeMount: Component DOM say pehle
onBeforeMount(() => {
    console.log('🧱 Component is about to mount')
})

// 🔹 onMounted: Component DOM ban gaya
onMounted(() => {
    console.log('✅ Component mounted and background set to lightblue')
    bgColor.value = 'lightblue'  // Set background to light blue when component mounts

    // Start a simple timer when the component is mounted
    timer = setInterval(() => {
        console.log('Timer is running...')
    }, 1000)
})

// 🔹 onBeforeUpdate: Reactivity update honay se pehle (e.g., when user types)
onBeforeUpdate(() => {
    console.log('✏️ Text is about to change...')
    bgColor.value = 'lightyellow'  // Change background color to light yellow when user types
})

// 🔹 onUpdated: Reactivity update ho chuki
onUpdated(() => {
    console.log('✅ Text has changed and background updated to light yellow')
})

// 🔹 onBeforeUnmount: Component hataane se pehle
onBeforeUnmount(() => {
    console.log('🧹 Component is about to unmount')
    clearInterval(timer)  // Stop the timer before unmounting
})

// 🔹 onUnmounted: Component delete ho chuka
onUnmounted(() => {
    console.log('❌ Component unmounted')
})
</script>

<template>
    <div :style="{ backgroundColor: bgColor }" class="p-4 border rounded max-w-md mx-auto mt-10">
        <h2 class="text-xl font-bold mb-2">🧪 Lifecycle Hooks Example</h2>
        <input v-model="message" placeholder="Type something..." class="border p-2 w-full rounded" />
        <p class="mt-2">You typed: <strong>{{ message }}</strong></p>
        <p>⏱️ Timer is running...</p>
    </div>
</template> -->
<script setup>
import { ref, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted } from 'vue'

// Reactive variables
const inputValue = ref('')
const isLoading = ref(false)
const counter = ref(0);

let btnSubmitRef = null;

// 🔹 onBeforeMount: Component mount hone se pehle
onBeforeMount(() => {
    console.log('🧱 Component DOM ke liye tayar ho raha hai')
    isLoading.value = true
})

// 🔹 onMounted: Component mount hone ke baad
onMounted(() => {
    console.log('✅ Component mounted, initial border color set')
    isLoading.value = false
})

// 🔹 onBeforeUpdate: User input change hone se pehle
onBeforeUpdate(() => {
    console.log('✏️ Input update hone wala hai')
    if (btnSubmitRef) {
        btnSubmitRef.style.borderColor = 'red'
    }
})

// 🔹 onUpdated: User input change hone ke baad
onUpdated(() => {
    console.log('✅ --------------- onUpdated')
    if (btnSubmitRef) {
        btnSubmitRef.style.backgroundColor = 'green'
    }
})

// 🔹 onBeforeUnmount: Component unmount hone se pehle
onBeforeUnmount(() => {
    console.log('🧹 Component remove hone se pehle cleanup')
})

// 🔹 onUnmounted: Component unmount hone ke baad
onUnmounted(() => {
    console.log('❌ Component unmounted, border reset')
})

const example = () => {
    console.log("Example without ()")
}

const example2 = (() => {
    console.log("Example with ()")
})

const incrementCounter = () => {
    counter.value++
}

const formattedCounterValue = computed(() => {
    return counter.value > 10 ? 'You have just crossed 10 digits' : 'You are lazy'
})

</script>

<template>
    <div class="p-4">
        <h2 class="text-lg font-bold mb-2">🔑 Input Field Example</h2>
        <input v-model="inputValue" :style="{ borderWidth: '2px', borderStyle: 'solid' }"
            placeholder="Type something..." class="p-2 w-full rounded" />
        <p class="mt-2">You typed: <strong>{{ inputValue }}</strong></p>
        <button @click="incrementCounter" ref="btnSubmitRef" class="text-black border-4 px-4 py-2 rounded">
            Counter = {{ counter }}
        </button>
        <p>{{ formattedCounterValue }}</p>

        <p @click="example">Example 1</p>
        <p @click="example2">Example 2</p>
    </div>
</template>
