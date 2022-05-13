<template>
  <div class="container">
    <div class="taskContainer">
      <p>{{ singleTask.description }} : {{ singleTask.done }}</p>
      <button
        class="btn btn--change"
        @click="changeStatus"
        v-if="singleTask.done"
      >
        Undone
      </button>
      <button class="btn btn--change" @click="changeStatus" v-else>Done</button>
      <button
        class="btn btn--delete"
        @click="
          () => {
            handleDeleteTask();
          }
        "
      >
        Delete
      </button>
    </div>
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

<style lang="scss">
.btn--change {
  background-color: #1ed760;
  width: 50px;
  height: 50px;
}
.btn--delete {
  background-color: rgb(145, 2, 2);
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
  &:hover {
    transform: scale(1.1);
  }
}

.taskContainer {
  display: flex;
  gap: 15px;
  font-size: 24px;
}

@media only screen and (max-width: 768px) {
  .taskContainer {
    flex-direction: column;
    align-items: center;
  }
}

@media only screen and (min-width: 1024px) {
}
</style>
