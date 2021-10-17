<template>
    <h1>tmdb detail page</h1>
</template>

<script>
import axios from 'axios'
export default {
    async fetch() {
      const { data } = await axios.get(`https://api.themoviedb.org/3/movie/{movie_id}?api_key=88c8e859d46625c472d014b2f3c995b0&language=en-US`)
      this.popularTvPrograms = data.results
      this.popularTvPrograms.map((item)=>{
          this.movieID.push(item.id)
          this.moviePosterPath.push(item.backdrop_path)
      })
    }
}
</script>