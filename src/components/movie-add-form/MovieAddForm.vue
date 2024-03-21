<template>
	<div class="movie-add-form">
		<h3>Yangi kino qoshish</h3>
		<from class="add-form d-flex" @submit.prevent>
			<Input
				type="text"
				class="form-control new-movie-label"
				placeholder="Qanday kino?"
				:value="name"
				@input="name = $event.target.value"
			/>
			<Input
				type="text"
				class="form-control new-movie-label"
				placeholder="Nechi marotaba ko'rilgan?"
				:value="viewers"
				@input="viewers = $event.target.value"
			/>
			<button class="btn btn-outline-dark" type="submit" @click="addMovie">Qo'shish</button>
		</from>
	</div>
</template>

<script>
export default {
	data() {
		return {
			name: "",
			viewers: "",
		};
	},
	methods: {
		addMovie() {
			if (!this.name || !this.viewers) return;
			const newMovie = {
				name: this.name,
				viewers: this.viewers,
				favourite: false,
				like: false,
				id: Date.now(),
			};
			this.$emit("createMovie", newMovie);
			this.name = "";
			this.viewers = "";
		},
	},
};
</script>

<style>
.movie-add-form {
	margin-top: 2rem;
	padding: 1.5rem;
	background-color: #10da13;
	box-shadow: 15px 15px 15px rgb(0, 0, 0, 0.15);
	border-radius: 4px;
}
</style>
