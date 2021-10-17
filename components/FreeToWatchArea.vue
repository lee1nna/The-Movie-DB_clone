<template>
    <div>
      <div class="content-header">
          <h3>Free to Watch</h3>
          <div id="category-selector">
            <ul>
              <li @click="clickFreeMovie">영화</li>
              <li @click="clickFreeTv">TV프로그램</li>
            </ul>
          </div>
        </div>
        <div class="slider-box">
        <div class="slider" v-show="FreeMovieShow" >
            <ul v-for="(item,i) in FreetoWatchMovie" :key="i">
            <nuxt-link :to="'/movie/'+FreetoWatchMovieID[i]"><li><img id="poster" :src="'https://image.tmdb.org/t/p/w200'+FreetoWatchMovie[i].poster_path" alt="poster"></li></nuxt-link>
            <nuxt-link :to="'/movie/'+FreetoWatchMovieID[i]"><li id="popular-tv-name"><a href="#">{{FreetoWatchMovie[i].title}}</a></li></nuxt-link>
            <li id="release-date">{{FreetoWatchMovie[i].release_date}}</li>
            </ul>
        </div>
        <div class="slider" v-show="FreeTvShow" >
            <ul v-for="(item,i) in FreetoWatchTv" :key="i">
            <nuxt-link :to="'/tv/'+FreetoWatchTvID[i]" ><li><img id="poster" :src="'https://image.tmdb.org/t/p/w200'+FreetoWatchTv[i].poster_path" alt="poster"></li></nuxt-link>
            <nuxt-link :to="'/tv/'+FreetoWatchTvID[i]" ><li id="popular-tv-name"><a href="#">{{FreetoWatchTv[i].name}}</a></li></nuxt-link>
            <li id="release-date">{{FreetoWatchTv[i].first_air_date}}</li>
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
        FreetoWatchMovie: [],
        FreetoWatchMovieID: [],
        FreetoWatchTv: [],
        FreetoWatchTvID: [],
        FreeTvShow : false,
        FreeMovieShow: true,
      }
    },
    async fetch() {
      const FreetvData = await axios.get(`https://api.themoviedb.org/3/discover/movie?api_key=88c8e859d46625c472d014b2f3c995b0&language=en-US&page=1&with_watch_monetization_types=free`)
      // console.log(FreetvData.data)
      this.FreetoWatchMovie = FreetvData.data.results
      this.FreetoWatchMovie.map((item)=>{
        this.FreetoWatchMovieID.push(item.id)
      })

      const FreemovieData = await axios.get(`https://api.themoviedb.org/3/discover/tv?api_key=88c8e859d46625c472d014b2f3c995b0&language=en-US&page=1&with_watch_monetization_types=free`)
      // console.log(FreemovieData.data.results)
      this.FreetoWatchTv = FreemovieData.data.results
        this.FreetoWatchTv.map((item)=>{
        this.FreetoWatchTvID.push(item.id)
      })
    },

    methods: {
      clickFreeMovie(){
        this.FreeTvShow = false
        this.FreeMovieShow = true
      },
      clickFreeTv(){
        this.FreeMovieShow = false
        this.FreeTvShow = true
      }
    }
  }
</script>
<style>
/* 
  *{
    margin: 0;
    padding: 0;
  }

  .main-title > h2{
    font-size: 24px;
    font-weight: 700;
    margin: auto;
    padding: 20px 0px 0px 10px;
    max-width:1300px;
  }

  .slider ul{
    width: 150px;
    display: inline-block;
    list-style: none;
    white-space: nowrap;
    padding: 0;
  }

  .slider li a{
    text-decoration: none;
    color: rgb(0, 0, 0);
  }

  .slider-box{
    max-width:1300px;
    padding-top: 10px;
    height: 305px;
    overflow: auto;
    white-space: nowrap;
    margin:0 auto;
  }

  #poster{
    width: 150px;
    height: 225px;
    padding: 10px;
    border-radius: 20px;
  }

  #popular-tv-name{
    font-size: 14px;
    font-weight: 700;
  }

  #release-date{
    font-size: 14px;
    font-weight: 500;
  } */

</style>