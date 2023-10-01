<!-- main.vue -->
<!-- single-file component, html + js + css -->

<!-- api style: OPTIONS API -->
<!-- define a component's logic using object of options such as `data`, `methods`, and `mounted` -->
<!-- properties defined by options are exposed on `this` inside functions, which points to the component instance -->
<script>
export default
{
    // properties returned from data() become reactive state
    // and will be exposed on `this`.
    data()
    { 
        return
        {
            count: 0
        }
    },

    // methods are functions that mutate state and trigger updates
    // they can be found as event handlers in templates
    methods:
    {
        increment()
        {
            this.count++
        }
    },

    // lifecycle hooks are called at different stages
    // of a component's lifecycle
    // this function will be called when the component is 'mounted'
    mounted()
    {
        console.log(`The initial count is ${this.count}.`)
    }
}
</script>

<template>
    <button @click="count++">Count is: {{ count }}</button>
</template>

<style scoped>
button {
    font-weight: bold;
    font-size: 24pt;
    font-family: 'Segoe', serif;
}
</style>