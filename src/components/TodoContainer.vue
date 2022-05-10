<template>
  <CreateTodo @createTodo="handleAddTodo($event)" />
  <div v-for="(Todo, i) in TodoList" :key="i">
    {{ Todo.description }} status:{{ Todo.done }}
    <button v-if="Todo.done">Undone</button>
    <button v-else>Done</button>
    <button>Delete</button>
  </div>
</template>

<script lang="ts">
import { Todo } from "@/models/Todo";
import { Options, Vue } from "vue-class-component";
import CreateTodo from "./CreateTodo.vue";

@Options({
  components: {
    CreateTodo,
  },
})
export default class TodoContainer extends Vue {
  TodoList: Todo[] = [new Todo("Äta"), new Todo("Gymma"), new Todo("Plugga")];

  handleAddTodo(t: Todo) {
    this.TodoList.push(t);
  }
}
</script>

<style lang="scss"></style>
