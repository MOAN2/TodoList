<template>
  <div>
    <h2>正在进行 <span id="num-doing" v-text="doingNum">0</span></h2>
    <div>
      <ul id="onList">
          <ItemDoing v-for="(doing) in doings" :key="doing.id" :doing="doing" :changeChecked='changeChecked' :delTodo="delTodo"  ></ItemDoing>
      </ul>
    </div>
  </div>
</template>

<script>
import ItemDoing from './ItemDoing.vue';
export default {
  components: { ItemDoing },
  name: "Doing",
  props:['doings','changeChecked','doingNum','delTodo'],
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
ul {
  list-style: none;
}
</style>