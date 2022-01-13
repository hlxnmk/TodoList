<script setup lang="ts">

import Header from './components/Header.vue';
import Lists from './components/Lists.vue';
import Footer from './components/Footer.vue';
import { reactive, provide } from 'vue';
import { Todo } from './types/todo'

const state = reactive<{ todos: Todo[] }>({
  todos: [
    { id: 1, title: '吃饭', isCompleted: false },
    { id: 2, title: '睡觉', isCompleted: true },
    { id: 3, title: '玩游戏', isCompleted: false },
  ]
})


provide('state', state) //给自己的后代组件传递数据
// 添加todo
const addTodo = (todo: Todo) => {
  state.todos.unshift(todo)
}
// 清除完成todo
const clearCompletedTodos = () => {
		state.todos = state.todos.filter(todo=>!todo.isCompleted)	
}
</script>

<template>
 <div >
    <Header :addTodo="addTodo" />
    <Lists />
    <Footer :todos="state.todos"  :clearCompletedTodos="clearCompletedTodos" />
  </div>
</template>

<style scoped>
div{
  width: 600px;
  margin: 0 auto;
}
</style>
