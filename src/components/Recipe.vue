<template>
	<div class="recipe-container">
		<p><u>Title:</u> {{title}}</p>
		<a :href="website" target="_blank">LINK</a>
		<p><u>Ingredients:</u> {{ingredients}}</p>
		<div><img :src="recImg"/></div>
	</div>
</template>

<script>
	export default {
		name: 'Recipe',
		props: ['title', 'website', 'ingredients', 'recImg'],
	}
</script>

<style scoped>
	.recipe-container {
		margin: 20px;
		padding: 20px;
		border: 22px solid #5caae6;
		border-top-left-radius: 10px;
		border-bottom-right-radius: 10px;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		width: 300px;
		height: 300px;
		background: rgb(52, 52, 52);
		transform: rotateZ(-4deg);
		box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
	}

	p, a {
		font-family: "Fira Code", sans-serif;
		color: whitesmoke;
	}
</style>
