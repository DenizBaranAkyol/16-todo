<template>
  <div class="container">
    <h3 class="text-center">Todo App</h3>
    <hr class="my-2">
    <AddSection @add-todo="addNewTodo" />
    <TodoList @delete-todo-item="deleteItem" :myData=" todoList " />
    <ResultBar :itemCount="todoList.length" />
    <button class="red sm">deneme</button>
  </div>
</template>

<script>

import AddSection from "@/components/AddSection.vue";
import TodoList from "@/components/TodoList.vue";
import ResultBar from "@/components/ResultBar.vue";

export default {

  components: {
    AddSection,
    TodoList,
    ResultBar
  },

  created() {
 setTimeout(() => {
      this.todoList = [
        { id: 1, text: "Bootcamp #2" },
        { id: 2, text: "Bootcamp #2.1" },
        { id: 3, text: "Bootcamp #2.2" },
        { id: 4, text: "Bootcamp #2.3" },
        { id: 5, text: "Bootcamp #2.4" },
        { id: 6, text: "Bootcamp #2.5" }
      ];
    }, 100);
 
  

},

data() {
  return {
    todoList: [],
    inputValue: null,
    addValue: null,
  };
},

methods: {

  deleteItem(todoItem){
    console.log(todoItem);
    this.todoList = this.todoList.filter(t => t != todoItem)
  },

  addNewTodo(event){
    this.todoList.push({
      id: new Date().getTime(),
      text: event
    })

   
    
  },
 

}


};



</script>