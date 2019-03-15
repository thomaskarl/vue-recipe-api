<template>
	<div>
		<div v-if="loaded">
			<div v-for="recipe in recipes.results">
				<Recipe v-bind:title="recipe.title"
						v-bind:website="recipe.href"
						v-bind:ingredients="recipe.ingredients"
						v-bind:recImg="recipe.thumbnail"
				></Recipe>
			</div>
		</div>
		<div v-else>
			<p>fetcing data</p>
			<button @click="beforeMount">Last tingene</button>
		</div>
	</div>
</template>

<script>
	import Recipe from './components/Recipe.vue'

	export default {
		name: 'app',
		components: {
			Recipe
		},
		data() {
			return {
				loaded: false,
				recipes: []
			}
		},

		mounted() {
			// this.beforeMount();
		},

		methods: {
			beforeMount: function () {
				const conversionUrl = 'https://cors-anywhere.herokuapp.com/';
				const url = 'http://www.recipepuppy.com/api/';

				fetch(conversionUrl + url)
					.then((response) => {
						return response.json();
					})
					.then((result) => {
						this.loaded = true;
						this.recipes = result;
					})
			}
		}
	}

</script>

<style>
#app {
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
}
</style>
