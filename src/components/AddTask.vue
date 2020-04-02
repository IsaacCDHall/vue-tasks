<template>
    <div>
        <form @submit.prevent="addTask">
            <input v-model="title" type='text' name='title' placeholder='Add Task ...'>
            <input type='submit'  value='Submit' class='btn'>
        </form>
    </div>
</template>
<script>
import {v4 as uuidv4} from 'uuid';
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
                id: uuidv4(),
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