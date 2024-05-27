<template>
  <div class="app container font-monospace">
    <div class="content">
      <AppInfo />

      <div class="search-panel block-panel">
        <SearchPanel />
        <AppFilter />
      </div>

      <MovieList />
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
};
</script>


<style></style>