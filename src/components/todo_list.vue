<template>
    <div class="main">
    <h1>Projeto Todo List</h1>
    <input v-model="todo" id="todo" name="todo" 
    @keyup.enter="add(todo)" placeholder="Adicione uma tarefa">

    <button @click="add(todo)" type="button">Adicionar</button>
    <ul>
        <li v-for="todo in todos" :key="todo" @dblclick="remove(todo)"    
        @click="complete(todo)"
        :class="todo.done && 'complete'">{{todo.name}}</li>  
    </ul>
    </div>
</template>

<script>
export default {
    name: 'ToDoList',

    data() {    //função q retorna um objeto
    return {
      id : 0, 
      todo : '', 
      todos : [] 
    }
    },
    methods: {

    genId() {
      return (this.id += 1); 
    },

    add(todo) {
        if (todo.trim().length) {

            this.todos.push({
              id: this.genId(), //gera um novo id
              name: todo,
              done: false, 
            });
            this.todo = ""; 
        } else {
            alert("Por favor, entre com caracteres validos")
        }
     
    },
    getIndex(todo) {
      //..recebe o todo como parâmetro, procura ele e retorna o seu index
      let index = this.todos.findIndex( item => item.id === todo.id );
      return index;      
    },
    remove(todo) {
      let index = this.getIndex(todo);
      this.todos.splice(index, 1);
    },
    //..recebe um todo como parâmetro de entrada muda seu status
    complete(todo) {
      todo.done = !todo.done;
    },
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Ubuntu:ital,wght@0,300;0,400;0,500;0,700;1,300;1,400;1,500;1,700&display=swap');

*{
    font-family: 'Ubuntu', sans-serif;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body{
  background: rgb(2,0,36);
  background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(9,9,121,1) 35%, rgba(0,212,255,1) 100%);
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px;
  margin: 0;
  width: 100vw;
  height: 100vh;
}

.main{
    background-color: #fff;
    max-width: 480px;
    width: 100%;
    max-height: 100%;
    padding: 25px;
    border-radius: 25px;
    overflow: auto;
    color: #222;
}
h1{
   font-size: 20px;
   line-height: 32px;
   margin: 0 0 12px 0;
   color: #272727; 
}

button {
    width: 25%;
    cursor: pointer;
    background: #f8f9fd;
    color: #272727;
    margin: 0.5rem;
    height: 45px;
    border-radius: 10px;
}
input{
    width: 65%;
    height: 45px;
    padding: 10px;
    background: #f8f9fd;
    color: #333;
    border-radius: 10px;
    transition: border 0.3s linear;
}

ul{
    color: blue;
    list-style: none;
   
}

li {
  cursor: pointer; 
}
.complete {
  text-decoration: line-through; 
  color: green; 
  
}
</style>