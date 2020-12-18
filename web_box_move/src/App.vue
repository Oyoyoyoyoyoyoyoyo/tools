<template>
  <div id="app">
    <box-move class="boxMoveBox"></box-move>
  </div>
</template>

<script>
import BoxMove from "./components/BoxMove";

export default {
  name: "App",
  components: {
    BoxMove,
  },
};
</script>

<style>
#app {
  width: 100%;
  height: 600px;
}
.boxMoveBox {
  width: 100%;
  height: 100%;
}
</style>
