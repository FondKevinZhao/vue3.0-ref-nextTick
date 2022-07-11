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
  组件的$nextTick(callback)方法，会把callback回调推迟到下一个DOM更新周期之后执行。
  通俗的理解是：等组件的DOM异步地重新渲染完成后，再执行callback回调函数。从而能保证callback回调函数可以操作到最新的DOM元素。
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
