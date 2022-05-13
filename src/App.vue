<template>
  <Loader v-if="isLoading" />
  <div v-else>
    <h1 class="titleText">Welcome to your Todo-List</h1>
    <h1 class="mobileText">Todo-List</h1>
    <TodoContainer />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Loader from "./components/Loader.vue";
import TodoContainer from "./components/TodoContainer.vue";

@Options({
  components: {
    TodoContainer,
    Loader,
  },
})
export default class App extends Vue {
  isLoading = true;

  mounted() {
    setTimeout(() => {
      this.isLoading = !this.isLoading;
    }, 2000);
  }
}
</script>

<style lang="scss">
body {
  font-family: "Courier New", Courier, monospace;
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

.titleText,
.mobileText {
  font-size: 48px;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  .titleText {
    display: none;
  }
}

@media only screen and (min-width: 768px) {
  .mobileText {
    display: none;
  }
}
</style>
