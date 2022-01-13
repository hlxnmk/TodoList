<script setup lang="ts">
import { inject,ref} from 'vue'

const state = inject('state')

const deleteTodo = (index) => {
	if (window.confirm('你确定要删除当前任务吗?'))
		state.todos.splice(index, 1)
}

const checked = ref(null)
// 改变复选框状态
const changeCheck = (index) => {
	state.todos[index].isCompleted = !state.todos[index].isCompleted
	if (state.todos[index].isCompleted) {
		checked.value = true
		state.todos[index].isCompleted=true
	} else {
		checked.value = false
		state.todos[index].isCompleted=false
	}
}
</script>

<template>
	<li v-for="(todo,index) in state.todos" :key="todo.id">
		<label>
			<input type="checkbox" :checked="todo.isCompleted" @click="changeCheck(index)" />
			<span>{{ todo.title }}</span>
		</label>
		<button @click="deleteTodo(index)" class="btn btn-danger">删除</button>
	</li>
</template>



<style scoped>
/*item*/
li {
	list-style: none;
	height: 36px;
	line-height: 36px;
	padding: 0 10px;
	border-bottom: 1px solid #ddd;
}

li label {
	float: left;
	cursor: pointer;
}

li label li input {
	vertical-align: middle;
	margin-right: 6px;
	position: relative;
	top: -1px;
}

li button {
	display: none;
	float: right;
	margin-top: 3px;
}

li:before {
	content: initial;
}

li:last-child {
	border-bottom: none;
}

li:hover {
	background-color: rgba(82, 168, 236, 0.8);
}

li:hover button {
	display: inline-block;
}

.btn {
	display: none;
	padding: 4px 12px;
	margin-bottom: 0;
	font-size: 14px;
	line-height: 20px;
	text-align: center;
	vertical-align: middle;
	cursor: pointer;
	box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2),
		0 1px 2px rgba(0, 0, 0, 0.05);
	border-radius: 4px;
}

.btn-danger {
	display: none;
	color: #fff;
	background-color: #da4f49;
	border: 1px solid #bd362f;
}

.btn-danger:hover {
	color: #fff;
	background-color: #bd362f;
}

.btn:focus {
	outline: none;
}
</style>