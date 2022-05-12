<template>
  <div class="container">
    <p>{{ singleTask.description }} : {{ singleTask.done }}</p>
    <button @click="changeStatus" v-if="singleTask.done">Undone</button>
    <button @click="changeStatus" v-else>Done</button>
    <button
      @click="
        () => {
          handleDeleteTask();
        }
      "
    >
      Delete
    </button>
  </div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Todo } from "@/models/Todo";
import { Prop } from "vue-property-decorator";
export default class TaskFunctions extends Vue {
  @Prop() singleTask!: Todo;

  changeStatus() {
    console.log("Du klickade");
    this.singleTask.done = !this.singleTask.done;
  }

  handleDeleteTask() {
    this.$emit("deleteTask", this.singleTask);
  }
}
</script>

<style></style>
