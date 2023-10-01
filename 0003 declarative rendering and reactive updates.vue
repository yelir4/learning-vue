<!-- using composition api -->
<!-- https://vuejs.org/tutorial/#step-2 -->

<script setup>
    import { ref, reactive } from 'vue'

    // component logic
    // declare some reactive state here.
    const counter = reactive({
        count: 0
    })
    
    const message = ref('Hello world!')
    
    console.log(message.value)
    message.value = 'where is the console?'
</script>

<!-- html side -->
<template>
    <!-- reactive state declared in <script setup> can be used directly in the template (html)
        Thus we can redner dynamic text based on value of `counter` object and `message` ref,
        using mustaches syntaxes ` {{  }} `
    -->
    
    <!--   <h1>Make me dynamic!</h1> -->

    <h1>
        <!-- note we dont need to say `message.value` ; it is automatically unwrapped -->
        {{ message }}
        <br>
        <!-- print in reverse -->
        {{ message.split('').reverse().join('') }}
    </h1>
    
    <p>
        count is :: {{counter.count}}
        <!-- {{ counter.count++ }} -->
    </p>
</template>