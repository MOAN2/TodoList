<template>
  <div>
      <nav>
        <div class="header">
            <div class="title">ToDoList</div>
            <input type="text" placeholder="在此处输入ToDo" class="insert" @keyup.enter="addTodo" v-model="title">
        </div>
    </nav>
  </div>
</template>

<script>
import { nanoid } from 'nanoid';
export default {
    name:"TodoInput",
    data() {
        return {
            title:""
        }
    },
    props:['getTodo'],
    methods: {
        addTodo(){
            if(this.title !=''){
                const todoObj = {id:nanoid(),title:this.title.trim(),completed:false}
                this.getTodo(todoObj)
                this.title=''
            }else{
                alert("输入不能为空")
                return;
            }
        }
    },
}
</script>

<style scoped>
  nav {
            width: 100%;
            height: 50px;
            line-height: 50px;
            font-size: 2rem;
            background: rgba(0, 5, 98, .7);
            color: white;
        }
        
        .header {
            width: 65rem;
            height: 50px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
        }
        
        .title {
            font-size: 3rem;
            cursor: pointer;
        }
        
        .insert {
            width: 35rem;
            height: 24px;
            margin-top: 12px;
            text-indent: 10px;
            border-radius: 5px;
            box-shadow: 0 1px 0 rgb(255 255 255 / 24%), 0 1px 6px rgb(0 0 0 / 45%) inset;
            border: 0px;
            outline: none;
            font-size: 1.5rem;
        }
</style>