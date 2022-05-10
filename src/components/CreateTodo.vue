<template>
  <h2>Create a new todo</h2>
  <form @submit.prevent="onSubmit">
    <input
      type="text"
      placeholder="Write a description"
      v-model="description"
      @keypress.enter="addTodo"
    />
    <button @click="addTodo">Save</button>
  </form>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Todo } from "@/models/Todo";

export default class CreateTodo extends Vue {
  description = "";

  addTodo() {
    console.log("Du klickade");
    this.$emit("createTodo", new Todo(this.description));
    this.description = "";
  }
}
</script>

<style lang="scss"></style>
