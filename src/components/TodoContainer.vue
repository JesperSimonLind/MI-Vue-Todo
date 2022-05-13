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
    localStorage.setItem("Todo", JSON.stringify(this.TodoList));
  }
  handleDeletedTask(todo: Todo) {
    this.TodoList.splice(this.TodoList.indexOf(todo), 1);
  }

  mounted() {
    if (localStorage.getItem("Todo") != null) {
      this.TodoList = JSON.parse(localStorage.getItem("Todo") || "[]");
    } else {
      return;
    }
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
