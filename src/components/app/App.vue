<template>
	<div class="app container font-monospace">
		<div class="content">
			<AppInfo :allMoviesCount="movies.length" :favouriteMoviesCount="movies.filter(c => c.favourite).length" />

			<div class="search-panel block-panel">
				<SearchPanel 
					:updateTermHandler="updateTermHandler"
				/>
				<AppFilter 
					:changeFilterHandler="changeFilterHandler"
				/>
			</div>

			<MovieList :movies="onFilterHandler(onSearchHandler(movies, term), filter)" @onToggle="onToggleHandler" @onDelete="onDeleteHandler" />
			<MovieAdd @createMovie="createMovie" @sequenceIdUpdate="sequenceIdUpdateHandler"
				:sequence_id="sequence_id" />
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
			term: "",
			filter: "all",
		}
	},
	methods: {
		createMovie(newMovie) {
			console.log(newMovie);
			this.movies.push(newMovie);
		},
		onToggleHandler({ id, prop }) {
			this.movies = this.movies.map(movie => {
				if (movie.id == id) {
					return { ...movie, [prop]: !movie[prop] };
				}
				return movie;
			});
		},
		onDeleteHandler(id) {
			this.movies = this.movies.filter(item => item.id != id);
		},
		sequenceIdUpdateHandler() {
			this.sequence_id += 1
		},
		onSearchHandler(arr, term){
			if (term.length == 0) return arr;

			return arr.filter(item => item.name.toLowerCase().includes(term));
		},
		updateTermHandler(term){
			this.term = term;
		},
		onFilterHandler(arr, filter){
			switch(filter){
				case "popular":
					return arr.filter(item => item.like);
				case "mostViews":
					return arr.filter(item => item.views >= 900);
				default:
					return arr;
			}
		},
		changeFilterHandler(filter){
			this.filter = filter;
		}
	}
};
</script>


<style></style>