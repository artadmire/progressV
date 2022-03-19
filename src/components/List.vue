<template>
	<ul>
		<li v-for="(i, index) in arr" :key="index">{{i}}</li>
	</ul>
</template>

<script>
export default {
  name: "List",
	data() {
		return {
			arr: []
		}
	},
	created() {
		for(let i = 0; i < 100000; i ++) {
			this.arr[i] = i;
		}
	}
};
</script>

