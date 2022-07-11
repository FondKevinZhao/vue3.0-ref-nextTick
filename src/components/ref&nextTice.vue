<template>
  <div>
    <h1>App 根组件</h1>
    <h2>需求：点击按钮让按钮消失，并且让光标在input框中</h2>
    <hr />
    <input type="text" v-if="inputVisible" ref="ipt" />
    <button type="button" v-else @click="showInput">展示input输入框</button>
  </div>
</template>

<script>
// 需求：点击按钮让按钮消失，并且让光标在input框中
/* 
  Vue生命周期的created()钩子函数进行的DOM操作一定要放在Vue.nextTick()的回调函数中，原因是在created()钩子函数执行的时候DOM 其实并未进行任何渲染，而此时进行DOM操作无异于徒劳，所以此处一定要将DOM操作的js代码放进Vue.nextTick()的回调函数中。与之对应的就是mounted钩子函数，因为该钩子函数执行时所有的DOM挂载已完成。
*/
export default {
  data() {
    return {
      inputVisible: false,
    };
  },
  methods: {
    showInput() {
      this.inputVisible = true;
      // this.$refs.ipt.focus(); // 不能直接写，否则会报错。为什么呢？因为DOM元素的更新时异步的
      this.$nextTick(function () {
        this.$refs.ipt.focus();
      });
    },
  },
};
</script>

<style>
</style>