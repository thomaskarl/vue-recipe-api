<template>
	<div id="app">
		<div v-for="recipe in recipes.results">
			<Recipe v-bind:title="recipe.title"
					v-bind:website="recipe.href"
					v-bind:ingredients="recipe.ingredients"
					v-bind:recImg="recipe.thumbnail"
			></Recipe>
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
				recipes: []
			}
		},
		beforeMount: function () {
			const app = this;

			const conversionUrl = 'https://cors-anywhere.herokuapp.com/';
			const url = 'http://www.recipepuppy.com/api/';

			fetch(conversionUrl + url)
				.then(function (response) {
					return response.json();
				})
				.then(function (result) {
					app.recipes = result;
				})
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
