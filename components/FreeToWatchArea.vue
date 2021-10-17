<template>
    <div>
      <div class="content-header">
          <h3>Free to Watch</h3>
          <div id="category-selector">
            <ul>
              <li><a href="#">영화</a></li>
              <li><a href="">TV프로그램</a></li>
            </ul>
          </div>
        </div>
        <div class="slider-box">
        <div class="slider">
            <ul v-for="(item,i) in popularTvPrograms" :key="i">
            <li><a href="#"><img id="poster" :src="'https://image.tmdb.org/t/p/w200'+popularTvPrograms[i].poster_path" alt="poster"></a></li>
            <li id="popular-tv-name"><a href="#">{{popularTvPrograms[i].original_title}}</a></li>
            <li id="release-date">{{popularTvPrograms[i].release_date}}</li>
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
        popularTvPrograms: []
      }
    },
    async fetch() {
      const { data } = await axios.get(`https://api.themoviedb.org/3/discover/movie?api_key=88c8e859d46625c472d014b2f3c995b0&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&with_watch_monetization_types=free`)
      this.popularTvPrograms = data.results
    },
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