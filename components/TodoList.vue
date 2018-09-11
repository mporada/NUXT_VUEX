<template>
  <b-list-group>
    <todo-list-item 
        v-for="todo in todos" 
        :key="todo.label" 
        :label="todo.label" 
        :todo-id="todo.id"
        :completed="todo.completed"></todo-list-item>
  </b-list-group>
</template>

<script>
    import Vue from 'vue';
  import bListGroup from "bootstrap-vue/es/components/list-group/list-group";
  import TodoListItem from "~/components/TodoListItem.vue";
  //import Axios from 'axios';
  

  export default {
    data() {
        return {

        }
    },
    props: {
        todos: {
            type: Array
        }
    },
    computed: {
        computedTodos: {
            get() {
                return this.todos ? this.todos : []
            },
            set() {}
        }
    },
    components: {
      "b-list-group": bListGroup,
      "todo-list-item": TodoListItem
    },
    mounted: async function(){
        
    },
    methods: {
        deleteTodo(id) {
            this.$emit('delete-todo', id)
        },
        
    }
  };

</script>

<style>
</style>
