<template>
   <header>
     <h1>{{title}}</h1>
     <Button @show-todo-form="$emit('show-todo-form')" 
     :text="changeButton ? 'Close' : 'Add Todo'" 
     :color="changeButton ? 'red': 'green' "/>
   </header>
</template>

<script>
import Button from './Button.vue'

    export default {
        name: 'header',
        props: {
            title: String,
            changeButton: Boolean
        },
        components: {
            Button
        }
    }

</script>


<style scoped>
  header {
    display: flex;
    justify-content: space-around;
    padding: 20px;
  }
</style>

