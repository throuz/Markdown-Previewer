<template>
  <h1 id="title">Markdown Previewer</h1>
  <HelloWorld />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import HelloWorld from "./components/HelloWorld.vue";

export default defineComponent({
  name: "App",
  components: {
    HelloWorld,
  },
});
</script>

<style>
#app {
  margin: 60px;
}
#title {
  text-align: center;
}
</style>