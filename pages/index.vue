<template>
  <div>
    <Header/>
    <h1>What's Popular</h1>
    <div class="slider-box">
      <div class="slider">
        <ul v-for="(item,i) in popularTvPrograms" :key="i">
          <li><a href="#"><img id="poster" :src="'https://image.tmdb.org/t/p/w200'+popularTvPrograms[i].poster_path" alt="poster"></a></li>
          <li id="popular-tv-name"><a href="#">{{popularTvPrograms[i].name}}</a></li>
          <li id="release-date">{{popularTvPrograms[i].first_air_date}}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

const popularTvPrograms = []

export default {
    asyncData({params, error}) {
      return axios.get(`https://api.themoviedb.org/3/tv/popular?api_key=88c8e859d46625c472d014b2f3c995b0&language=en-US&page=1`)
      .then((res)=>{
        return {
          popularTvPrograms: res.data.results
      }
      })
      .catch((e)=>{
        console.log(e)
      })
    },
  }
</script>
<style>

  *{
    margin: 0;
    padding: 0;
  }

  .slider-box ul{
    width: 150px;
    display: inline-block;
    list-style: none;
    white-space: nowrap;
  }

  a{
    text-decoration:none;
    color:inherit;
  }

  .slider-box{
    max-width:1300px;
    height: 300px;
    overflow: auto;
    white-space: nowrap;
    margin:0 auto;
  }

  #poster{
    width: 130px;
    border-radius: 10px;
  }

  #popular-tv-name{
    font-size: 14px;
    font-weight: 700;
  }

  #release-date{
    font-size: 14px;
    font-weight: 500;
  }

</style>