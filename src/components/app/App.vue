<template>
	<div class="app font-monospace">
		<div class="content">
			<Appinfo
				:allMoviesCount="movies.length"
				:favouriteMoviesCount="movies.filter((c) => c.favourite).length"
			/>
			<div class="search-panel">
				<SearchPanel :updateTermHandler="updateTermHandler" />
				<AppFilter :updateFilterHandler="updateFilterHandler" :filterName="filterName" />
			</div>
			<MovieList
				:movies="onFilterHandler(onSearchHandler(movies, term), filter)"
				@onToggle="onToggleHandler"
				@onRemove="onRemoveHandler"
			/>
			<MovieAddForm @createMovie="createMovie" />
		</div>
	</div>
</template>
y
<script>
import Appinfo from "@/components/app-info/Appinfo.vue";
import SearchPanel from "@/components/search-panel/SearchPanel.vue";
import AppFilter from "@/components/app-filter/AppFilter.vue";
import MovieList from "@/components/movie-list/MovieList.vue";
import MovieAddForm from "@/components/movie-add-form/MovieAddForm.vue";
export default {
	components: {
		Appinfo,
		SearchPanel,
		AppFilter,
		MovieList,
		MovieAddForm,
	},
	data() {
		return {
			movies: [
				{
					name: "Sevgi Istirobi",
					viewers: 811,
					favourite: false,
					like: true,
					id: 1,
				},
				{
					name: "Qalbaki o’yin",
					viewers: 600,
					favourite: false,
					like: false,
					id: 2,
				},
				{
					name: "Qogozz    bino ",
					viewers: 200,
					favourite: true,
					like: false,
					id: 3,
				},
			],
			term: "",
			filter: "all",
		};
	},
	methods: {
		createMovie(item) {
			this.movies.push(item);
		},
		onToggleHandler({ id, prop }) {
			this.movies = this.movies.map((item) => {
				if (item.id == id) {
					return { ...item, [prop]: !item[prop] };
				}
				return item;
			});
		},
		onRemoveHandler(id) {
			this.movies = this.movies.filter((c) => c.id !== id);
		},
		onSearchHandler(arr, term) {
			if (term.length == 0) {
				return arr;
			}
			return arr.filter((c) => c.name.toLowerCase().indexOf(term) > -1);
		},
		onFilterHandler(arr, filter) {
			switch (filter) {
				case "popular":
					return arr.filter((c) => c.like);
				case "mostViewers":
					return arr.filter((c) => c.viewers > 500);

				default:
					return arr;
			}
		},
		updateTermHandler(term) {
			this.term = term;
		},
		updateFilterHandler(filter) {
			this.filter = filter;
		},
	},
};
</script>

<style>
.app {
	height: 100vh;
	color: black;
}
.content {
	width: 1000px;
	min-height: 700px;
	background-color: #fff;
	margin: 0 auto;
	padding: 5rem 0;
}
.search-panel {
	margin-top: 2rem;
	padding: 1.5rem;
	background-color: #10da13;
	box-shadow: 15px 15px 15px rgb(0, 0, 0, 0.15);
	border-radius: 4px;
}
</style>

<!-- <template>
	<div class="container">
		<h1>Counter: {{ counter }}</h1>
		<div class="d-flex">
			<button @click="onIncrement" class="btn btn-success">Add</button>
			<button @click="onDecrement" class="btn btn-danger">Delete</button>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			counter: 0,
		};
	},
	methods: {
		onIncrement() {
			this.counter += 1;
		},
		onDecrement() {
			this.counter -= 1;
		},
	},
};
</script>
 -->
