<template>
    <div class="home">
        <div class='titleAndInput'>
            <div class="titleText">T o d o ?</div>
            <a-input class="input" v-on:input='todoInput' v-bind:value='inputTodo' placeholder='what could you want to do?' style="height: 80px; width: 450px; align-self: center; font-size: 30px;"/>
            <div class="button">
                <a-button class='add' v-on:click='addToList' type="primary" style="height: 70px; width: 160px; align-self: center; font-size: 30px;">Add</a-button>
            </div>
            <div class='icon'>
                <img src="../components/mao.png" style="width: 200px; height: 200px;">
            </div>
          </div>
          <todoList v-bind:list='todoTotheList' />
    </div>
</template>

<script>
    import todoList from './sonComp/todoList.vue'

    const beforeCreate  = () => {
        document.querySelector('body').setAttribute('style', 'background-color:#ffc0cb;')
    }
    beforeCreate ()

    export default {
        name: "Home",
        data() {
            return {
                placeholderText: 'what could you want to do?',
                inputTodo: '',
                todoTotheList: [],
            }
        },
        methods: {
            todoInput: function(event) {
                let value = event.target.value
                this.inputTodo = value
                console.log('value is ', value)
            },
            addToList: function() {
                let todo = this.inputTodo
                if(todo === '') {
                    alert('plz input')
                }
                var list = this.todoTotheList
                list.push(todo)
                this.inputTodo = ''
                console.log('todo is', this.todoTotheList)
            }
        },
        components: {
            todoList,
        },
    }
</script>

<style>
    .titleAndInput {
        width: 60%;
        height: 100vh;
        border-right: 2px rgb(242, 243, 241) solid;
        display: flex;
        flex-direction: column;
    }
    .titleText {
        font-size: 100px;
        font-family: 'Gill Sans';
        margin-top: 190px;
        margin-bottom: 20px;
    }
    .button {
        margin-top: 50px;
    }
    .icon {
        text-align: left;
    }
</style>