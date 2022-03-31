<template>
  <div>
    <h2>全部事项 <span id="num-all" v-text="allNum">0</span></h2>
  </div>
</template>

<script>
export default {
  name: "AllTodo",
  props:['allNum']
};
</script>

<style scoped>
h2 {
  position: relative;
}
span {
  position: absolute;
  top: 2px;
  right: 5px;
  display: inline-block;
  padding: 0 5px;
  height: 20px;
  border-radius: 20px;
  background: #e6e6fa;
  line-height: 22px;
  text-align: center;
  color: #666;
  font-size: 14px;
}
</style>