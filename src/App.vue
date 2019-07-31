<template>
    <div id="app">
        <TodoHeader></TodoHeader>
        <TodoInput v-on:addTodo="addTodo"></TodoInput>
        <TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
        <TodoFooter v-on:clearTodo="clearTodo"></TodoFooter>
    </div>
</template>

<script>
    import TodoHeader from './components/TodoHeader'
    import TodoInput from './components/TodoInput'
    import TodoList from './components/TodoList'
    import TodoFooter from './components/TodoFooter'

    export default {

        data() {
            return {
                todoItems: []
            }
        },
        methods: {
            addTodo(todoItem) {
                localStorage.setItem(todoItem, todoItem);
                this.todoItems.push(todoItem);
            },
            removeTodo(todoItem, index){
              localStorage.removeItem(todoItem);
              this.todoItems.splice(index, 1);
            },
            clearTodo() {
              localStorage.clear();
              this.todoItems = [];
            }
        },
        created() {
            if (localStorage.length > 0) {
                for (var i = 0; i < localStorage.length; i++) {
                    this.todoItems.push(localStorage.key(i));
                }
            }
        },
        components: {
            'TodoHeader': TodoHeader,
            'TodoInput': TodoInput,
            'TodoList': TodoList,
            'TodoFooter': TodoFooter
        }
    }
</script>

<style>
    body {
        text-align: center;
        background-color: #f6f6f8;
        font-family: 'Ubuntu', sans-serif;
        font-family: 'Noto Sans KR', sans-serif;
    }

    input {
        border-style: groove;
        width: 200px;
    }

    button {
        border-style: groove;
    }

    .shadow {
        box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03)
    }
</style>