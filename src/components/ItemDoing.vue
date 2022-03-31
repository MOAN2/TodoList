<template>
  <div>
    <li id="onLi">
      <input
        type="checkbox"
        class="doing"
        :checked="doing.completed"
        @change="isChecked(doing.id)"
      />
      <p>{{ doing.title }}</p>
      <a @click="del(doing.id)">-</a>
    </li>
  </div>
</template>

<script>
export default {
  name: "ItemDoing",
  props: ["doing", "changeChecked", "delTodo"],
  methods: {
    isChecked(id) {
      // console.log(id);
      //可以直接修改 但原则上在数组原组件上修改
      // this.todo.done= !this.todo.done;
      this.changeChecked(id);
    },
    del(id) {
      if(confirm('确认删除吗？'))
      {
         this.delTodo(id)
      }
     
    },
  },
};
</script>

<style scoped>
li {
  height: 32px;
  line-height: 32px;
  background: #fff;
  position: relative;
  margin-bottom: 10px;
  padding: 0 45px;
  border-radius: 3px;
  border-left: 5px solid #629a9c;
  box-shadow: 0 1px 2px rgb(0 0 0 / 7%);
}
li input {
  position: absolute;
  top: 2px;
  left: 10px;
  width: 22px;
  height: 22px;
  cursor: pointer;
}

li a {
  position: absolute;
  top: 2px;
  right: 5px;
  display: inline-block;
  width: 14px;
  height: 12px;
  border-radius: 14px;
  border: 6px double #fff;
  background: #ccc;
  line-height: 14px;
  text-align: center;
  color: #fff;
  font-weight: bold;
  font-size: 14px;
  cursor: pointer;

  /* 默认删除按钮隐藏 */
  display: none;
}
#onLi:hover{
  background-color: rgba(98,154,156, .3)
}
#onLi:hover a{
  display: block;
}
</style>