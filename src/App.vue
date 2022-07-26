<script>
import Stack from './views/Stack.vue'
import Queue from './views/Queue.vue'

export default {
	components: {
		Stack,
		Queue
	},
	data() {
		return {
			active: true
		}
	}
}
</script>

<template>
<button class="mode" @click="active = !active">{{ active ? 'Queue' : 'Stack' }}</button>
<div v-if="active"><Stack/></div>
<div v-else><Queue/></div>
</template>

<style scoped>
.mode {
	width: 10%;
	height: 3em;
	margin: auto;
	background-color: var(--secondary);
	color: aliceblue;
	border-radius: 0 50vh 50vh 0;
	position: relative;
	top: 30px;

}

@media only screen and (max-width: 700px) {
	.mode {
		width: 20%;
	}
}
</style>

