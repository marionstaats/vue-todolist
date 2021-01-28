<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>{{todo.title}}</p>
        <input type="checkbox" v-on:change="markComplete" >
        <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete(){
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background-color: rgb(168, 154, 154);
        padding: 10px;
        border-bottom: 1px dotted;
    }
    .is-complete {
        text-decoration: line-through;
    }
    .del {
        background-color: red;
        color: white;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>