<!-- https://vuejs.org/tutorial/#step-6 -->

<!--
    `v-if` directive is used to conditionally render elements

    ex:
        <h1 v-if="awesome">vue is awesome</h1>
        <h1 v-else> oh god no 😢🧼🧼🧼</h1>
    
    is rendered only if `awesome` 's value is truthy

-->

<script setup>
    import { ref } from 'vue'

    const awesome = ref(true)

    function toggle()
    {
        if(awesome.value == true)
        {
            awesome.value = false;
        }
        else
        {
            awesome.value = true;
        }
    }
</script>

<template>
    <!--
        this demo shows both <h1> at the same time, while the button is dysfunctional
    -->
    <button @click="toggl">useless demo</button>
    <h1>Vue is awesome!</h1>
    <h1>Oh no 😢</h1>

    <!--
        so we will add v-if and v-else directives,
        and we will also implement the toggle() method in js so that
        we can use the button to toggle between them
    -->

    <button @click="toggle">toggle</button>
    <h1 v-if="awesome">Vue is awesome!</h1>
    <h1 v-else>Oh no 😢</h1>
</template>