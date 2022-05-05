<template>
    <form @submit="onSubmit">
        <div class="desc-input control">
            <label for="task">Task: </label>
            <input type="text" placeholder="What is next?" class="input" v-model="description" name="description">
        </div>
        <div class="task-time control" >
            <label for="time">Time: </label>
            <input type="text" placeholder="At what time?" class="input" v-model="time" name="time" >
        </div>
        <div class="reminder control">
            <label for="reminder">Reminder:</label>
            <input type="checkbox" v-model="reminder" name="reminder" >
        </div>
        <input type="submit" value="Save" class="control butt">
    </form>
</template>


<script>
export default {
    name: 'AddTodo',
    data(){
        return {
            description: '',
            time: '',
            reminder: false
        }
    },
    methods: {
        onSubmit(e){
            e.preventDefault()

            if(!this.description){
                alert('add task des')
                return
            }

            const newTodo = {
                id: Math.floor(Math.random() * 100000),
                description: this.description,
                time: this.time,
                reminder: this.reminder
            }

            this.$emit('add-task', newTodo)

            this.description = ''
            this.time = ''
            this.reminder = ''
        }
    }
}

</script>



<style>
    .control {
        margin: 10px;
    }
    .input {
        width: 300px;
        height: 35px;
        border: 0;
        border-radius: 5px;
    }
    .butt {
    background-color: green;
    color: #fff;
    border: none;
    padding: 10px 10px;
    border-radius: 5px;
    height: 35px;
    width: 80px;
    margin-left: 8rem;
    }

    form {
        margin-left: 5rem;
    }

    ::placeholder {
        font-style: italic;
        font-size: 12px;
    }
</style>