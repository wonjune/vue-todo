<template>
    <div class="clearAllContainer shadow">
        <span class="clearAllBtn" @click="clearTodo">Clear All</span>
    </div>
</template>

<script>
    export default {
        methods: {
            clearTodo() {
                this.$emit('clearTodo');
            }
        }
    }
</script>

<style>
    .clearAllContainer {
        width: 8.5rem;
        height: 50px;
        line-height: 50px;
        background-color: white;
        border-radius: 5px;
        margin: 0 auto;
    }

    .clearAllBtn {
        color: #e20303;
        display: black;
    }
</style>