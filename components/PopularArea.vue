<template>
    <div>
      <div class="content-header">
          <h3>What's Popular</h3>
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
            <nuxt-link :to="'/tv/'+popularTvID[i]" ><li><img id="poster" :src="'https://image.tmdb.org/t/p/w200'+popularTvPrograms[i].poster_path" alt="poster"></li></nuxt-link>
            <li id="popular-tv-name"><a href="#">{{popularTvPrograms[i].name}}</a></li>
            <li id="release-date">{{popularTvPrograms[i].first_air_date}}</li>
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
        popularTvID : [],
      }
    },
    async fetch() {
      const { data } = await axios.get(`https://api.themoviedb.org/3/tv/popular?api_key=88c8e859d46625c472d014b2f3c995b0&language=en-US&page=1`)
      this.popularTvPrograms = data.results
      this.popularTvPrograms.map((item)=>{
        this.popularTvID.push(item.id)
      })

    console.log(this.popularTvID)
    },
  }
</script>
<style>

  *{
    margin: 0;
    padding: 0;
  }

  ul{
    list-style: none;
  }

  a{
    text-decoration: none;
    outline: none;
  }

  .content-header{
    width: 1300px;
    height: 40px;
    margin: 0 auto;
    margin-top: 20px;
    padding: 30px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .content-header h3{
    font-size: 24px;
    font-weight: 700;
    top: 20px;
    margin: 0;
  }

  .content-header ul {
    margin: 0;
    width: 100%;
    height: 100%;
    display: flex;
  }

  .content-header ul > li {
    font-size: 15px bold;
    height: 100%;
    display: flex;
    text-align: left;
    margin: 0px 20px 0px 20px;
  }

  .content-header ul > li :hover{
    color: rgb(255, 145, 0);
  }

  .content-header ul > li a {
    text-decoration: none;
    color: rgb(0, 0, 0);
  }

  .content-header > #category-selector{
    position: relative;
    right: 800px;
    bottom: 13px;
    height: 100%;
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
    height: 350px;
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
    padding-left: 20px;
  }

  #release-date{
    font-size: 14px;
    font-weight: 500;
    padding-left: 20px;
  }

</style>