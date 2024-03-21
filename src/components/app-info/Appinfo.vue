<template>
	<div class="app-info">
		<p class="fs-3 text-uppercase">Barcha kinolar soni:{{ allMoviesCount }}</p>
		<p class="fs-4 text-uppercase">Ko'rilgan kino son:{{ favouriteMoviesCount }}</p>
	</div>
</template>

<script>
export default {
	props: {
		allMoviesCount: {
			type: Number,
			required: true,
		},
		favouriteMoviesCount: {
			type: Number,
			required: true,
		},
	},
};
</script>

<style scoped>
.app-info {
	padding: 1.5rem;
	background-color: #10da13;
	box-shadow: 15px 15px 15px rgb(0, 0, 0, 0.15);
	border-radius: 4px;
}
</style>
