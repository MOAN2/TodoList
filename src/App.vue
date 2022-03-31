<template>
  <div id="app">
    <!-- 输入todo -->
    <todo-input :getTodo="getTodo"></todo-input>

    <section>
      <all-todo :allNum="this.todos.length "></all-todo>
      <doing
      :doings="doings" 
      :changeChecked="changeChecked" 
      :doingNum="this.doings.length" 
      :delTodo="delTodo"></doing>

      <done 
       :dones="dones"
       :changeChecked="changeChecked" 
       :doneNum="this.dones.length" 
       :delTodo="delTodo"></done> 
    </section>
  </div>
</template>

<script>
import AllTodo from "./components/AllTodo.vue";
import Doing from "./components/Doing.vue";
import Done from "./components/Done.vue";
import TodoInput from "./components/TodoInput.vue";

export default {
  name: "App",
  components: {
    TodoInput,
    Doing,
    Done,
    AllTodo,
  },
  data() {
    return {
      todos: [],
      doings:[],
      dones: [],
    };
  },
  methods: {
    getTodo(todoObj) {
      this.todos.unshift(todoObj);
      this.doings.unshift(todoObj);
    },
    changeChecked(id) {
      this.todos.forEach((todo) => {
        if (todo.id == id) {
          //如果done为true，则是已完成列表
          if(todo.completed){
          
            //将true改为false，未勾选
            todo.completed = !todo.completed;

            //将todo添加到doing中
            this.doings.unshift(todo);
         
            //删除完成的事项
            this.dones = this.todos.filter(todo => todo.completed )

            // console.log("取消完成");
          }else{
             //将false改为true，勾选
            todo.completed = !todo.completed;        

            //将todo添加到done中
            this.dones.unshift(todo)   

            //删除正在进行的事项
            this.doings = this.todos.filter(todo => !todo.completed )

            // console.log("完成");
          }
        } 
      });
    },
    delTodo(id){
       this.todos.forEach((todo) => {
            if (todo.id == id) {
                //如果done为true，则是已完成列表
              if(todo.completed){
                this.dones = this.dones.filter(todo => todo.id != id)
              }else{
                 this.doings = this.doings.filter(todo => todo.id != id)
              }
            }
       })     
    }
  }
};
</script>

<style >
@media screen and (max-width: 600px) {
  /*最大为600*/
  html {
    font-size: 40%;
  }
}

@media screen and (min-width: 600px) {
  html {
    font-size: 50%;
  }
}

body {
  margin: 0;
  padding: 0;
  font-size: 2rem;
  background: #f1f1f1;
}

ul {
  list-style: none;
}
section {
  margin: 0 auto;
  width: 65rem;
}
</style>