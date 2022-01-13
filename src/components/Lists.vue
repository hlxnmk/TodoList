<script setup lang="ts">
import Item from './Item.vue';


</script>

<template>
	<div class="todo-wrap">
		<ul class="todo-main">
			<Item  />			
		</ul>
	</div>
</template>


<style scoped>
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>