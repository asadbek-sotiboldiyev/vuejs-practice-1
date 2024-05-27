<template>
	<div class="app container font-monospace">
		<div class="content">
			<AppInfo :allMoviesCount="movies.length" :favouriteMoviesCount="movies.filter(c => c.favourite).length" />

			<div class="search-panel block-panel">
				<SearchPanel />
				<AppFilter />
			</div>

			<MovieList :movies="movies" @onLike="onLikeHandler" />
			<MovieAdd @createMovie="createMovie" />
		</div>
	</div>
</template>

<script>
import AppInfo from '../app-info/AppInfo.vue';
import SearchPanel from '../search-panel/SearchPanel.vue';
import AppFilter from '../app-filter/AppFilter.vue';
import MovieList from '../movie-list/MovieList.vue';
import MovieAdd from '../movie-add/MovieAdd.vue';

export default {
	components: {
		AppInfo, SearchPanel, AppFilter, MovieList, MovieAdd
	},
	data() {
		return {
			movies: [
				{ id: 1, name: 'Terminator', views: 899, favourite: true, like: false },
				{ id: 2, name: 'Qasoskorlar', views: 901, favourite: false, like: false },
				{ id: 3, name: 'Kelajakka qaytib', views: 900, favourite: false, like: true },
				{ id: 4, name: 'Avatar', views: 1000, favourite: false, like: false },
			],
			sequence_id: 4,
		}
	},
	methods: {
		createMovie(newMovie) {
			console.log(newMovie);
			this.movies.push(newMovie);
		},
		onLikeHandler(id) {
			this.movies = this.movies.map(item => {
				if (item.id == id) {
					item.like = !item.like;
				}
				return item;
			});
		},

	}
};
</script>


<style></style>