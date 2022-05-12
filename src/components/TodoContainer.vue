<template>
  <div class="container">
    <CreateTodo @createTodo="handleAddTodo($event)" />
    <TaskFunctions
      @deleteTask="handleDeletedTask"
      v-for="t in TodoList"
      :key="t"
      :singleTask="t"
    />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import { Todo } from "@/models/Todo";
import CreateTodo from "./CreateTodo.vue";
import TaskFunctions from "./TaskFunctions.vue";

@Options({
  components: {
    CreateTodo,
    TaskFunctions,
  },
})
export default class TodoContainer extends Vue {
  TodoList: Todo[] = [new Todo("Äta"), new Todo("Gymma"), new Todo("Plugga")];

  handleAddTodo(t: Todo) {
    this.TodoList.push(t);
  }
  handleDeletedTask(todo: Todo) {
    console.log("hej");
    this.TodoList.splice(this.TodoList.indexOf(todo), 1);
  }
}
</script>

<style lang="scss">
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
