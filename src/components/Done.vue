<template>
  <div>
    <h2>已经完成 <span id="num-done" v-text="doneNum">0</span></h2>
    <div>
      <ul id="downList">
        <item-done v-for="done in dones " :key="done.id" :done="done"  :changeChecked='changeChecked' :delTodo="delTodo"></item-done> 
   
      </ul>
    </div>
  </div>
</template>

<script>
 
import ItemDone from './ItemDone.vue';
export default {
  components: { ItemDone },
  name: "Done",
  props:['dones','changeChecked','doneNum','delTodo']
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

.dark {
  border-left: 5px solid rgb(128, 128, 128);
  opacity: 0.5;
}
</style>