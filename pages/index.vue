<template>
  <section class="container">
    <div>
      <todo-form v-on:add-todo="addTodo"></todo-form>
      <todo-list :todos="todos"></todo-list>
    </div>
  </section>
</template>

<script>
import Vue from 'vue';
import TodoList from "~/components/TodoList.vue"
import TodoForm from "~/components/TodoForm.vue"
import Axios from 'axios';

export default {
  data() {
    return {}
  },

  computed: {
    todos(){
      return this.$store.getters.todos
    }
  },
  components: {
    "todo-list": TodoList,
    "todo-form": TodoForm
  },
  mounted: async function () {
        //let response = await Axios.get('/todos.json')
        //Vue.set(this, "todos", this.$store.getters.todos)
    },
  methods: {
    addTodo(label) {
      if (label.length < 3 ) {
        alert("Please provide at least 3 characters")
      }
      else {
        let newTodos = this.todos
        newTodos.push({id: this.generateId(), label: label, completed: false})
        Vue.set(this, "todos", newTodos)
      }
    },
    generateId() {
      let id = 0
      this.todos.forEach(todo => {
        todo.id >  id ? id = todo.id : id
      });
      return id + 1
    }
  }
};
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

