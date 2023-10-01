<!-- https://vuejs.org/tutorial/#step-3 -->

<script setup>
    import { ref, reactive } from 'vue'

    // reference the 'title' in the css portion
    const titleClass = ref('title')

    const regularText = ref('regular')

    // more testing
    const moneyTracker = reactive({
        count: 0
    })
</script>

<template>
    <h1 v-bind:class="titleClass">Make me red</h1> <!-- add dynamic class binding here -->
    <!-- simple alternative: ` :class="titleClass" ` -->


    <!--
        now i want to understand so i do more testing
        ` :id="regularText" ` sends us to the javascript above, where we have regularText that defines it as 'regular' which takes us to the css portion
        wherein #regular is defined as the id and has modifiers to change the text within the <div>
    -->
    <div :id="regularText">
        <p>what is going on? {{moneyTracker.count}}</p>
    </div>
</template>

<style>
	/*  `.title` is a class selector ex: ` div :class="" `  */
    .title {
    color: red;
    }

    /*
        this is meant to be an id selector
    */
    #regular {
        width: 100px;
    	font-size: 24px;
        color: blue;
    }
</style>