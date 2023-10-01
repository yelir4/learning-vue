<!-- main.vue -->
<!-- single-file component, html + js + css -->

<!-- api style: COMPOSITION API -->
<!-- uses <script setup>, `setup` being an attribute that makes Vue perform compile-time transforms -->
<!-- this allows us to use Composition API with less boilerplate -->
<!-- ex: imports and top-level variables/functions declared in <script setup> are directly usable in the template -->
<!-- same component as in `optionsAPI.vue` but using Composition API, <script setup> -->
<script setup>
import { ref, onMounted } from 'vue'

// reactive state
const count = ref(0)

// functions that mutate state and trigger updates
function increment()
{
    count.value++
}

// lifecycle hooks
onMounted(() => {
    console.log(`The initial mount is ${count.value}.`)
})
</script>



<!-- html -->
<template>
    <button @click="increment">Count is: {{ count }}</button>
</template>





<!-- css -->
<style scoped>
button {
    font-weight: bold;
    font-size: 24pt;
    font-family: 'Segoe', serif;
}
</style>