<template>
  <div id="app" class="container ">
    <div id="todo">
        <h1 id="titulo" >Todo List Vue <img src="src/img/lista-de-verificacion.png" alt="todoIcon" width="40px"></h1>

    <div id="tarea">
        <h2 class="mt-2">{{message}}</h2>
        <div class="agregar row">
          <input type="text" v-model="todo" placeholder="Ingresa una nueva tarea" class="col" @keyup.enter="add_todo">
        <button v-on:click=add_todo class=" btn button-coral "> Agregar </button>
        </div>

        <ul class="px-0">
          
            <li v-for="(todo, index) in todos"
                :todo="todo" 
                :index="index"
                :key="todo.id" 
                >
                <span class="hearts">
                   &hearts;
                </span>
               
                    {{todo}}
                    <delete-component :id="index" @remove="remove_todo"></delete-component>
 
            </li>
        </ul>
    </div>

    </div>
  
  </div>


</template>
<script>
import remove from "./components/deleteComponent.vue"
  export default {
      data() {
      return {
        message: "Crea una nueva tarea",
        todos:[],
        todo:"",
    };
    },
    components:{
      'delete-component':remove,
      },
    methods:{
        add_todo: function (todo, index) { 
            if(this.todo != ""){
            this.todos.push(this.todo)
            this.todo="";
            }
        },
        remove_todo(todo){
           const todoIndex = this.todos.indexOf(todo);
            this.todos.splice(todoIndex, 1);
        }
    }
  }
</script>

<style >
li{
    text-decoration: none;
    list-style: none;
}
h1{
    font-size: 30px;
}
h2{
    font-size: 20px;
}

#todo{
    border: 2px solid coral;
    padding: 1em;
    margin: auto
}

.button-coral{
    background-color: coral;
    color: white;
}

i{
    color: lightpink;
    cursor: pointer;
    float: right;
    margin-top: 4px;
}

.hearts{
color: lightpink;
}

li{
    border-bottom: 1px solid coral;
    margin-top: 2px;
}

.agregar{
    margin: auto
}
</style>