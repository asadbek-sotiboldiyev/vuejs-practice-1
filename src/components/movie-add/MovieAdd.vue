<template>
	<div class="block-panel">
		<h2>Yangi kino qo'shish</h2>
		<form class="add-form d-flex" @submit.prevent>
			<input type="text" class="form-control" placeholder="Kino nomi" :value="name" @input="name = $event.target.value">
			<input type="text" class="form-control" placeholder="Ko'rilgan" :value="views"
				@input="views = $event.target.value">
			<button class="btn btn-outline-dark" @click="addMovie">Qo'shish
			</button>
		</form>
	</div>
</template>

<script>
export default {
	data() {
		return {
			name: "",
			views: "",
		}
	},

	methods: {
		addMovie() {
			const newMovie = {
				name: this.name,
				views: this.views,
				favourite: false,
				like: false
			};
			this.$emit('createMovie', newMovie);
			this.name = "";
			this.views = "";
		}
	}
};
</script>

<style scoped>
* {
	font-size: 20px;
}
</style>