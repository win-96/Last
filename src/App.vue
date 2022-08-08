<template>
	<div id="app">

		<!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
		<!-- <Home></Home> -->
		<!-- <Index></Index> -->
		<Last></Last>
	</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Home from './components/home.vue'
import Index from './components/index.vue'
import Last from './components/Last.vue'
export default {
	name: 'App',
	components: {
		HelloWorld,
		Home,
		Index,
		Last
	}
}
</script>

<style lang="less">
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
