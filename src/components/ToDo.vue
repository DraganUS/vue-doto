<template>
    <div id="ToDo">
        <div class="form">
            <input id="checkAll" @click="checkAll()" type="checkbox">
            <input @keyup.enter="addTodo" type="text" placeholder="What do you need to do?" v-model="newTodo">
            <button type="reset" @click="clearList(index)">Clear list</button>
        </div>
        <ul v-for="(value, index) in tasks" key="tasks.id">
            <li>
                <input type="checkbox" :checked="value.completed" @click="checkboxToggle(value)" >
                <span class="taskText">
                    <div v-if="!value.editing" @dblclick="editTodo(value)" :class="{ strike : value.completed }">{{ value.text }}</div>
                    <input v-else type="text" v-model="value.text" @dblclick="doneEdit(value)" @blur="doneEdit(value)" @keyup.enter="doneEdit(value)">
                </span>
                <button class="close" @click="remove(index)">X</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "ToDo",
    data () {
        return {
            newTodo: '',
            idForTodo: 3,
            tasks: [
                {
                    "id": 0, 
                    "text": "This is some finish task",
                    "completed": false,
                    "editing": false
                },
                {
                    "id": 1,
                    "text": "This is new task",
                    "completed": false,
                    "editing": false
                },
                {
                    "id": 2,
                    "text": "This is some task",
                    "completed": false,
                    "editing": false
                }
            ],
            remove(index) {
                this.tasks.splice(index, 1);
            },
            checkAll() {
                if (document.getElementById('checkAll').checked == true) {
                    for (let i = 0; i < this.tasks.length; i++) {
                        this.tasks[i].completed = true;
                    }
                }
                else {
                    for (let i = 0; i < this.tasks.length; i++) {
                        this.tasks[i].completed = false;
                    }
                }
            }
        }
    },
    methods: {
        clearList(index){
            this.tasks.splice(0, this.tasks.length);    
        },
        addTodo(){
            this.tasks.push({
                id: this.idForTodo,
                text: this.newTodo,
                completed: false
            })

            this.newTodo = '',
            this.idForTodo++
        },
        editTodo(value){
            value.editing = true;
        },
        doneEdit(value){
            value.editing = false;
        },
        checkboxToggle(value){
            if (value.completed === false) {
            value.completed = true;    
            } else{
                value.completed = false;    
            }
            
        }

    }
}
</script>

<style>
    .form,
    ul li {
        padding: 10px;
        width: 500px;
        margin: 0 auto;
    }

    .form {
        background-color: #eee;
    }
    ul:hover{
        cursor: pointer;
    }
    ul li:hover{
        background-color: rgba(22, 116, 192, 0.8);
    }

    input[type="text"] {
        width: 70%;
        height: 34px;
        padding: 0;
    }

    .form input[type="checkbox"] {
        position: relative;
        left: -15px;
    }

    button {
        background-color: #fff;
        border: 1px solid gray;
        height: 40px;
        padding: 0 20px;
        display: block;
        float: right
    }

    ul {
        list-style-type: none;
        padding: 0;
        margin: 0;
    }

    li {
        display: flex;
        justify-content: space-between;
        background-color: rgb(50, 116, 192);
        color: #fff;
        font-weight: bold;
        border-bottom: 1px solid #fff;
    }

    li:nth-last-of-type() {
        border-bottom: none;
    }

    .taskText {
        width: 86%;
        text-align: left
    }

    .close {
        visibility: visible;
        transition: .6s;
        padding: 0;
        margin: 0;
        background-color: transparent;
        height: auto;
        border: none;
        color: white;
    }    

    .strike {
        text-decoration: line-through;
    }

</style>
