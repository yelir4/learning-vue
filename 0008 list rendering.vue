<!-- https://vuejs.org/tutorial/#step-7 -->

<!--
    `v-for` directive renders list of elements based on a source array

    <ul>
        <li v-for="todo in todos" :key="todo.id">
            {{ todo.text }}
        </li>
    </ul>

    well we've seen this syntax before, essentially iterates through each element
    in `todos` and will render it within the mustaches
    <ul> being the unordered list and <li> being the list element


    anyway `todo` is only accessible on or inside the v-for element,
    similar to a function scope

    we also give each todo object a unique `id`, binding it as the special
    key attribute for each <li>

    this allows vue to accurately move each <li> to match the position
    of its corresponding object in the array

    now we can update the list by calling `mutating methods` on the source array
    todos.value.push(newTodo)

    or by replaceing the array with a new one
    todos.value = todos.value.filter(/* ... */)


    below we have a simple todo list and i have to
    implement the logic for addTodo() and removeTodo() methods to make it work
-->

<script setup>
    import { ref } from 'vue'

    // give each todo a unique id
    let id = 0

    // specific todo that we are iterating on right now?
    // i think its specifically helpful for ` vmodel="newTodo" `
    const newTodo = ref('')



    // list of todos
    const todos = ref([
        { id: id++, text: 'Learn HTML' },
        { id: id++, text: 'Learn JavaScript' },
        { id: id++, text: 'Learn Vue' }
    ])

    function addTodo() {
        // so the push syntax will be that we create a new entry
        // wherein the id increments itself, and the text value
        // is that of newTodo which is being dynamically updated within
        // <input v-model="newTodo">
        todos.value.push({id: id++, text: newTodo.value})


        // here they reset newTodo to '' as such
        // newTodo.value = ''
    }



    /* here's the way that they did it

        function removeTodo(todo) {
            todos.value = todos.value.filter((t) => t !== todo)
        }

        a lot simpler right? t being index within the array,
        remaking the array such that every t is there as long as
        t !== todo that was passed in

        but im confused how they get the key `todo.id` to automatically fix itself?
        that must be in the documentation but its kind of frustrating this tutorial
        step kind of leaves you dry LOL but ok

        well i tested with the following
            let index=0
    
            while(index < id)
            {
                todos.value[index].text = todos.value[index].id.toString()
                index++
            }
        

        and it works i guess? filter() somehow arbitrarily keeps the id() fine

        NO LOL IT ACTUALLY DOESNT WORK
        like the `id` isnt kept sequential after you do the filter
        ...
        i dont think thats good practice but what do i know
        that type of thing probably some recruiter would be like oh see how simple
        your code would be if you did just this

        but its spaghetti code LOLOL stupid
        i mean i get that iterating through the whole code to fix the id is probably
        inefficient if its only the ordering matters but then its more of the fault
        that the implementation calls for id within the array if theres no built
        in function that will maintain sequential ordering to begin with...
    */

    // removeTodo() removes `todo` from the list
    function removeTodo(todo) {
        // index will be the index of the array that we are deleting
        let index = todo.id
        // remove todo from the list using array splice()
        // splice at the given index, for just one entry
        todos.value.splice(index, 1)

      	// we need to decrement id
      	id--
        // now we have to update the ids
        // starting from the index that we spliced at,
        // through the end of the array, decrement the ids
        // alternative to id: todos.value.length
        while(index < id)
        {
            todos.value[index].id = index
            // testing purposes
          	// todos.value[index].text = todos.value[index].id
          	index++
        }
    }
</script>

<template>
    <!--
        having this @submit.prevent here
        is good because either pressing enter within the input box
        or pressing the button calls addTodo()
    -->
    <form @submit.prevent="addTodo">
        <!--
            syntax sugar for <input :value="newTodo" @input="addTodo">
            but apparently not? not @input="addTodo", it just changes newTodo
            automatically so we no longer need an event listener for it
        -->
        <input v-model="newTodo">
        <button>Add Todo</button>    
    </form>
    <ul>
        <li v-for="todo in todos" :key="todo.id">
            <!-- remember we have todo.id -->
            {{ todo.text }} <!-- {{ todo.id }} -->
            <button @click="removeTodo(todo)">X</button>
        </li>
    </ul>
  
    <!-- i will add this here to display the `id` aka todos' length -->
  	{{ id }}
</template>