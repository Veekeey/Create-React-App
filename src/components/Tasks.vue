<template>
    <div>
        <div :key="task.id" v-for="task in tasks">
            <task @toggle-reminder="$emit('toggle-reminder', task.id)" 
            @delete-task="$emit('delete-task', task.id)" 
            :task="task"/> 
        </div>
    </div>
</template>

<script>
    import task from './task'

export default {
    name: 'Tasks',
    props: {
        tasks: Array
    },
    components: {
        task
    },
    emits: ['delete-task', 'toggle-reminder']
}
</script>


<style>

</style>