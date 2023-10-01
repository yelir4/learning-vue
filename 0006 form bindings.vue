<!-- https://vuejs.org/tutorial/#step-5 -->
<script setup>
    import { ref } from 'vue'

    const text = ref('')

    function onInput(e) {
        text.value = e.target.value
    }
</script>

<!-- 
    using v-bind and v-on together, we can create two-way
    bindings on form input elements

    ex: <input :value="text" @input="onInput">

    function onInput(e)
    {
        // a v-on handler receives native DOM event as argument
        text.value = e.target.value
    }


    vue provides directive `v-model` which is syntax sugar for
    <input v-model="text">

    ^ automatically syncs <input>'s value with bound state
    works not only with text inputs but other input types as well
 -->

<template>
    <!-- 
        look how interesting is
        first, :value="text"
            sends us above where text is defined to an empty reference ref('')
            by changing the '' to have something, we can start with initial text
            within this text input box
        @input="onInput"
            sends us to above eventlistener onInput(e) which changes `text.value`
            to the argument e.target.value
            essentially '' becomes whatever is in the input box,
            so the <p> remember inside that is {{ text.value }} but its simplified
            supposedly? maybe its not text.value
     -->
    <input :value="text" @input="onInput" placeholder="Type here">
    <p>{{ text }}</p>

    <!-- so here's the refactored implementation which instead uses v-model -->
    <!-- same as above but just simplified visually -->
    <input v-model="text" placeholder="refactored input box uses v-model instead">
    <p> {{ text }}</p>
</template>