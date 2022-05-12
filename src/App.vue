<template>
  <h1>Welcome to your Todo-List</h1>
  <TodoContainer />
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import TodoContainer from "./components/TodoContainer.vue";

@Options({
  components: {
    TodoContainer,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
body {
  height: 100vh;
  background-color: rgb(15, 15, 15);
  padding: 0px;
  margin: 0px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: white;
}

h1 {
  font-size: 48px;
}
</style>
