<template>
    <div>
        <form @submit.prevent="addTodo">
            <input type="text" v-model="title" name="title" placeholder="AddTodo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>    
    
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
    name: 'AddTodo',
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo() {
            const uuid = uuidv4();
            const newTodo = {
                id: uuid,
                title: this.title,
                completed: false
            }
            this.$emit('add-todo', newTodo);
            this.title = '';
        }
        
    }
}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>