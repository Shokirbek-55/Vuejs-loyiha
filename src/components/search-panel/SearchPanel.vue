<template>
	<div>
		<input
			type="text"
			class="form-control search-input"
			placeholder="Kinolarni qidirish"
			:value="term"
			@input="changeHandler"
		/>
	</div>
</template>

<script>
export default {
	props: {
		updateTermHandler: {
			type: Function,
			required: true,
		},
	},
	data() {
		return {
			term: "",
		};
	},
	methods: {
		changeHandler(e) {
			this.term = e.target.value;
			this.updateTermHandler(this.term);
		},
	},
};
</script>

<style scoped>
.search-input {
	margin-bottom: 1rem;
	padding: 1rem;
	background-color: #fcfaf5;
	box-shadow: 15px 15px 15px rgb(0, 0, 0, 0.15);
	border-radius: 4px;
}
</style>
