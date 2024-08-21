<template>
  <div class="container-movies d-middle p-100 ">
    <CardMovie 
      v-for="movie in listMovies"
      :id= "movie.imdbID"
      :poster= "movie.Poster"
      :year="movie.Year"
      :title="movie.Title"
      :type="movie.Type"
    />
  </div>

</template>

<script setup lang="ts">
  import HTTP from "@/api/client-http"
  import type { ApiResponse, Movie } from "@/model/movie.model";
  import { onMounted, ref } from "vue";
  import CardMovie from "./CardMovie.vue";

  const listMovies = ref<Movie[]>([])

  onMounted(()=>{
    fetchMovies()    
  })

  const fetchMovies = async ()=>{
    const response: ApiResponse = await HTTP.get("",{
      params: {
        s: "movies",
      }
    })
    listMovies.value = response.data.Search;
    
  }
</script>


<style scoped lang="scss">
.container-movies{
  flex-wrap: wrap;
  justify-content: space-around;
  gap: 20px;
}

</style>