<template>
	<ul class="movie-list list-group">
		<MovieListItem
			v-for="movie in movies"
			:movie="movie"
			:key="movie.id"
			@onToggle="$emit('onToggle', $event)"
			@onRemove="$emit('onRemove', $event)"
		/>
	</ul>
</template>

<script>
import MovieListItem from "../movie-list-item/MovieListItem.vue";
export default {
	components: { MovieListItem },
	props: {
		movies: {
			type: Array,
			required: true,
		},
	},
};
</script>

<style scoped>
.movie-list {
	margin-top: 2rem;
	padding: 2rem;
	background-color: #10da13;
	box-shadow: 15px 15px 15px rgb(0, 0, 0, 0.15);
	border-radius: 4px;
}
</style>
