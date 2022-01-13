<script setup lang="ts">
import { nanoid } from 'nanoid'
import {ref} from 'vue'

const props = defineProps<{ addTodo:Function }>(	
)
const title =ref('')
// const id = ref(nanoid())
// 添加数据
const add =()=>{
	const text =title.value
	if(!text.trim())return
	// 准备数据
	const todo ={
		id:nanoid(),
		title:text,
		isCompleted:false
	}
	// 调用App里addTodo的方法
	props.addTodo(todo)
	// 清空输入
	title.value =''
}

</script>

<template>
	<div class="todo-header">
		<input v-model="title" @keyup.enter="add" type="text" placeholder="请输入你的任务名称，按回车键确认" />
	</div>
</template>



<style>
/*header*/
.todo-header input {
	width: 583px;
	height: 28px;
	font-size: 14px;
	border: 1px solid #ccc;
	border-radius: 4px;
	padding: 4px 7px;
}

.todo-header input:focus {
	outline: none;
	border-color: rgba(82, 168, 236, 0.8);
	box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
		0 0 8px rgba(82, 168, 236, 0.6);
}
</style>