<template>
      <b-list-group-item class="todo-list-item" :class="{completed: completed}">
          <input 
            class="float-left"
            type="checkbox"
            :value="completed"
            :checked="completed"
            @change="markTodo(todoId)"
        >
        {{ label }}
          <b-button class="float-right" size="size" variant="danger" @click="deleteTodo(todoId)">
                Delete
            </b-button>
      </b-list-group-item>
</template>

<script>
import bListGroupItem from "bootstrap-vue/es/components/list-group/list-group-item";
import bButton from 'bootstrap-vue/es/components/button/button';

export default {
  props: 
    {
        todoId: {
            type: Number,
            default: 0
        },
      label: {
        type: String,
        default: ""
      },
      completed: {
          type: Boolean,
          default: false
      }
    },
  components: {
    "b-list-group-item": bListGroupItem,
    "b-button": bButton
  },
  methods: {
    deleteTodo(id) {
        this.$store.commit('deleteTodo', id)
    },
    markTodo(id) {
      this.$store.commit('markTodo', id)
    }
  }
};
</script>

<style>
.todo-list-item { 
    min-width: 400px;
}

.todo-list-item.completed {
    opacity: 0.5;
    text-decoration: line-through;
}
</style>

