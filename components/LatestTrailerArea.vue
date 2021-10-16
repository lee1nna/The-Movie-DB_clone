<template>
    <div>
        <div class="main-title">
            <h2>최신 예고편</h2>
        </div>
        <div class="movie-slider-box">
            <div class="movie-slider">
                <ul v-for="(item,i) in videoKey" :key="i">
                <li>
                    <video id="latest-poster" :poster="'https://image.tmdb.org/t/p/w200'+moviePosterPath[i]" alt="poster" autoplay loop controls>
                    <iframe :src="'https://www.youtube.com/embed/'+videoKey[i]+'?autoplay=1'" frameborder="0" allowfullscreen wmode="Opaque"></iframe>
                    </video>
                </li>
                <li id="latest-movie-name"><a href="#">{{popularTvPrograms[i].original_title}}</a></li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {

    data() {
      return {
        popularTvPrograms: [],
        movieID: [],
        videoKey: [],
        moviePosterPath: [],
        movieName: [],
      }
    },

    async fetch() {
      const { data } = await axios.get(`https://api.themoviedb.org/3/movie/upcoming?api_key=88c8e859d46625c472d014b2f3c995b0&language=ko-KR&page=1`)
      this.popularTvPrograms = data.results
      this.popularTvPrograms.map((item)=>{
          this.movieID.push(item.id)
          this.moviePosterPath.push(item.backdrop_path)
      })
      
      let movieURL1 = `https://api.themoviedb.org/3/movie/${this.movieID[0]}/videos?api_key=88c8e859d46625c472d014b2f3c995b0`
      let movieURL2 = `https://api.themoviedb.org/3/movie/${this.movieID[1]}/videos?api_key=88c8e859d46625c472d014b2f3c995b0`
      let movieURL3 = `https://api.themoviedb.org/3/movie/${this.movieID[2]}/videos?api_key=88c8e859d46625c472d014b2f3c995b0`
      let movieURL4 = `https://api.themoviedb.org/3/movie/${this.movieID[3]}/videos?api_key=88c8e859d46625c472d014b2f3c995b0`
      let movieURL5 = `https://api.themoviedb.org/3/movie/${this.movieID[4]}/videos?api_key=88c8e859d46625c472d014b2f3c995b0`
    
      const promise1 = axios.get(movieURL1)
      const promise2 = axios.get(movieURL2)
      const promise3 = axios.get(movieURL3)
      const promise4 = axios.get(movieURL4)
      const promise5 = axios.get(movieURL5)
      let movieData = []
      
      await Promise.all([promise1, promise2, promise3, promise4, promise5]).then(values => {
          movieData = values
      })

      movieData.map((item)=>{
          this.videoKey.push(item.data.results[0].key)
      })
        console.log(this.videoKey)
    },

    methods: {
        playVideo(){
            
        }
    }
    
  }
</script>
<style>

  .movie-slider-box{
    max-width:1300px;
    padding-top: 10px;
    height: 400px;
    overflow: auto;
    white-space: nowrap;
    margin:0 auto;
  }

  .movie-slider ul{
    width: 150px;
    display: inline-block;
    list-style: none;
    white-space: nowrap;
    margin-right: 250px;
  }

  .movie-slider li a{
    text-decoration: none;
    color: rgb(0, 0, 0);
  }

  #latest-poster{
    position: relative;
    width: 350px;
    height: 225px;
    margin: 50px;
    border-radius: 20px;
  }

  #latest-movie-name{
    position: relative;
    left: 130px;
    bottom: 30px;
    text-align: center;
    font-size: 14px;
    font-weight: 700;
  }

</style>