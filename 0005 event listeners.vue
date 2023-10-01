<!-- https://vuejs.org/tutorial/#step-4 -->
<script setup>
    import { ref } from 'vue'

    // ref() is simply referencing some undefined thing (in css?)
    // so what ever is in the () is the initial value
    const count = ref(4)

    // we make increment function to implement the v-on that we made below
    // when this function is called by any object, it runs
    // incrementing count's value (the initial value of which is 4)
    function increment() {
        count.value++
    }
</script>

<template>
    <!--
        make this button work
        so we will use the `v-on` directive
    -->

    <button v-on:click="increment">count is: {{ count }}</button>
    <!-- shorthand alternative: <button @click="increment"> -->
    <button @click="increment">g{{ count.value }}</button>
</template>