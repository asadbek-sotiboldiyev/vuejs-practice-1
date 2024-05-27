<template>
  <div class="app container font-monospace">
    <div class="content">
      <AppInfo 
        :allMoviesCount="movies.length"
        :favouriteMoviesCount="movies.filter(c => c.favourite).length"
      />

      <div class="search-panel block-panel">
        <SearchPanel />
        <AppFilter />
      </div>

      <MovieList :movies="movies"/>
      <MovieAdd />
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
        { name: 'Terminator', views: 899, favourite: true, like: false },
        { name: 'Qasoskorlar', views: 901, favourite: false, like: false },
        { name: 'Kelajakka qaytib', views: 900, favourite: false, like: true },
        { name: 'Avatar', views: 1000, favourite: false, like: false },
      ],
    }
  }
};
</script>


<style></style>