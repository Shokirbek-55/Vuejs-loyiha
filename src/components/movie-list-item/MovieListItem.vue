<template>
	<li
		class="list-group-item d-flex justify-content-between"
		:class="[{ like: movie.like }, { favourite: movie.favourite }]"
	>
		<span
			@click="$emit('onToggle', { id: movie.id, prop: 'like' })"
			class="list-group-item-label"
			>{{ movie.name }}</span
		>
		<input type="number" class="list-group-item-input" v-bind:value="movie.viewers" />

		<div class="d-flex justify-content-center align-items-center">
			<button
				type="button"
				class="btn-cookie btn-sm"
				@click="$emit('onToggle', { id: movie.id, prop: 'favourite' })"
			>
				<i class="fas fa-cookie"></i>
			</button>

			<button type="button" class="btn-trash btn-sm" @click="$emit('onRemove', movie.id)">
				<i class="fas fa-trash"></i>
			</button>
			<i class="fas fa-star"></i>
		</div>
	</li>
</template>

<script>
export default {
	props: {
		movie: {
			type: Object,
			required: true,
		},
	},
	methods: {
		onLike() {
			this.$emit("onLike", this.movie.id);
		},
	},
};
</script>

<style scoped>
.list-group-item {
	border: none;
	padding: 15px 20px;
	border-bottom: 1px solid #3d5a80;
}

.list-group-item:last-child {
	border-bottom: none;
}
.list-list-group-item span {
	line-height: 35px;
	font-size: 20px;
	cursor: pointer;
	width: 550px;
}
.list-group-item input {
	line-height: 35px;
	font-size: 20px;
	text-align: center;
	border: 0;
	outline: none;
}
.list-group-item button {
	width: 35px;
	height: 35px;
	margin: 3px;
	font-size: 17px;
	border: none;
	cursor: pointer;
}
.list-group-item .btn-cookie {
	color: #06ac08;
}
.list-group-item .btn-trash {
	color: red;
}
.list-group-item .fa-star {
	width: 30px;
	height: 30px;
	text-align: center;
	line-height: 35px;
	font-size: 22px;
	color: #0d00ff;
	transition: 0.3s all;
	transform: translateX(30px);
	opacity: 0;
}
.list-group-item.like .fa-star {
	opacity: 1;
	transform: translateX(0);
}

.list-group-item.favourite .list-group-item-label {
	color: #06ac08;
}
.list-group-item.favourite .list-group-item-input {
	color: #06ac08;
}
</style>
