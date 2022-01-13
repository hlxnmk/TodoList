<script setup lang="ts">
import { computed } from 'vue';
const props = defineProps<{todos: Array<any>,
	clearCompletedTodos:Function}>(
	
)


// 使用计算属性 统计完成的数量
const completed = computed(() => {
	let count = 0
	props.todos.forEach(e => {
		e.isCompleted ? count++ : 0
	})
	return count
})

// 设置全选
const isCheckAll = computed({
	get() {
		return completed.value > 0 && props.todos.length === completed.value
	},
	set(value) {
		props.todos.forEach(e => {
			e.isCompleted = value
		})
	}

})

</script>

<template>
	<div class="todo-footer">
		<label>
			<input type="checkbox" v-model="isCheckAll" />
		</label>
		<span>
			<span>已完成{{ completed }}</span>
			/ 全部{{ props.todos.length }}
		</span>
		<button class="btn btn-danger" @click="clearCompletedTodos">清除已完成任务</button>
	</div>
</template>



<style >
/*footer*/
.todo-footer {
	height: 40px;
	line-height: 40px;
	padding-left: 6px;
	margin-top: 5px;
}

.todo-footer label {
	display: inline-block;
	margin-right: 20px;
	cursor: pointer;
}

.todo-footer label input {
	position: relative;
	top: -1px;
	vertical-align: middle;
	margin-right: 5px;
}

.todo-footer button {
	float: right;
	margin-top: 5px;
}
.btn {
	display: inline-block;
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