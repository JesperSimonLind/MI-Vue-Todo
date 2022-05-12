<template>
  <form class="createContainer" @submit.prevent="onSubmit">
    <input
      type="text"
      placeholder="Write a description"
      v-model="description"
    />
    <button class="btn btn--save" @click="addTodo">Save</button>
  </form>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Todo } from "@/models/Todo";
import { Prop } from "vue-property-decorator";

export default class CreateTodo extends Vue {
  @Prop() saveBtn!: string;
  description = "";

  addTodo() {
    console.log("Du klickade");
    this.$emit("createTodo", new Todo(this.description));
    this.description = "";
  }
}
</script>

<style lang="scss" scoped>
input {
  border: none;
  border-radius: 5px;
  background-color: white;
  height: 50px;
  width: 250px;
  text-align: center;
}
.btn--save {
  background-color: #1e99d7;
  width: 50px;
  height: 50px;
}

.btn {
  border: none;
  color: white;
  height: 50px;
  width: 100px;
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.createContainer {
  display: flex;
  gap: 15px;
  margin-bottom: 25px;
}
</style>
