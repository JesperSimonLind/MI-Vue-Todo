<template>
  <div class="container">
    <div class="text">
      <h1>Loading...</h1>
    </div>
    <div class="loading">
      <div class="line-box">
        <div class="line"></div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";

export default class Loader extends Vue {}
</script>

<style lang="scss">
.container {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.loading .line-box {
  padding: 2px;
  width: 225px;
  height: 20px;
  border: 2px solid white;
  border-radius: 20px;
}

.loading .line-box .line {
  height: 20px;
  border-radius: 20px;
  background: #1ed760;
  animation: loading 1.25s forwards cubic-bezier(0, 0, 0, 0);
}

@keyframes loading {
  0% {
    width: 0%;
  }
  100% {
    width: 100%;
  }
}
</style>
