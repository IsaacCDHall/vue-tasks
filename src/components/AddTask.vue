<template>
    <div>
        <form @submit.prevent="addTask">
            <input v-model="title" type='text' name='title' placeholder='Add Task ...'>
            <input type='submit'  value='Submit' class='btn'>
        </form>
    </div>
</template>
<script>
import uuid from 'uuid';
export default {
    name: 'AddTask',
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTask(){
            const newTask = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            }
            // Send up to parent
            this.$emit('add-task', newTask);
            this.title = '';
        }
    }
}
</script>
<style scoped>
    form {
        display:flex;
    }
    input[type='text'] {
        flex: 10;
        padding: 5px;
    }
    input[type='submit'] {
        flex: 2;
    }
    
</style>