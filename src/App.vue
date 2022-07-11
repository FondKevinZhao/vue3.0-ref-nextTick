<template>
  <div>
    <Son></Son>
  </div>
</template>

<script>
// 需求：点击按钮让按钮消失，并且让光标在input框中
import Son from "@/components/ref&nextTice";
export default {
  name: "App",
  components: {
    Son,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
