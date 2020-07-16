<template>
    <div class="listArea">
        <div class="listTitle"> TODO LIST </div>
            <h3 v-if='empty'>空空如也...</h3>
            <li v-for='single in todoTotheList'></li>
            <!-- <singleTodo v-if='todo'></singleTodo> -->
    </div>
</template>

<script>
    export default {
        name: 'todoList',
        data: function() {
            return {
                empty: true,
            }
        },
        props: [
            'todoTotheList'
        ],
        methods: {
            listContentBy: function() {
                if (!todoTotheList) {
                this.empty= true
                } else {
                    this.empty = false
                }
            },
        },
        template: `
        <div class='singleTodo'>
            <div class='todoContent' v-bind:value='todos'></div>
        </div>
        `
    }
</script>

<style>
    .listArea {
        width: 30%;
        height: 60vh;
        text-align: right;
    }
</style>