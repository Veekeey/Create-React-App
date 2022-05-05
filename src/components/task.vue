<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>{{task.description}} <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i></h3>
        <p>{{task.time}}</p>
    </div>
    
</template>

<script>
export default {
    name: 'task',
    props: {
        task: Object
    }
}
</script>


<style>
    .task {
        background-color: #fff;
        margin: 5px;
        padding: 5px 5px;
        height: 80px;
        border: 2px solid #eee;
    }

    .task.reminder {
        border-left: 3px solid green;
        border-radius: 5px;
    }
    
    .task h3 {
        display: flex;
        justify-content: space-between;
    }

    .fas {
        color: red;
        margin-right: 5rem;
    }
</style>