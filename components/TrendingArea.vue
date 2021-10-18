<template>
    <div>
      <div class="content-header">
          <h3>Trending</h3>
          <div id="category-selector">
            <ul>
              <li @click="clickToday">오늘</li>
              <li @click="clickWeek">이번주</li>
            </ul>
          </div>
        </div>
        <div class="slider-box">
          <div class="slider" v-show="weekShow" >
              <ul v-for="(item,i) in weekTrend" :key="i">
              <li><img id="poster" :src="'https://image.tmdb.org/t/p/w200'+weekTrend[i].poster_path" alt="poster"></li>
              <li id="popular-tv-name"><a href="#">{{weekTrend[i].name}}{{weekTrend[i].title}}</a></li>
              <li id="release-date">{{weekTrend[i].release_date}}{{weekTrend[i].first_air_date}}</li>
              </ul>
          </div>
          <div class="slider" v-show="todayShow" >
              <ul v-for="(item,i) in todayTrend" :key="i">
              <li><img id="poster" :src="'https://image.tmdb.org/t/p/w200'+todayTrend[i].poster_path" alt="poster"></li>
              <li id="popular-tv-name"><a href="#">{{todayTrend[i].name}}{{todayTrend[i].title}}</a></li>
              <li id="release-date">{{todayTrend[i].release_date}}{{todayTrend[i].first_air_date}}</li>
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
        todayTrend: [],
        todayTrendID : [],
        weekTrend: [],
        weekTrendID: [],
        todayShow : true,
        weekShow : false,
        tvNameShow : false,
        movieTitleShow : false
      }
    },

    async fetch() {
      const todayTrendData = await axios.get(`https://api.themoviedb.org/3/trending/all/day?api_key=88c8e859d46625c472d014b2f3c995b0`)
      this.todayTrend = todayTrendData.data.results
      this.todayTrend.map((item)=>{
        this.todayTrendID.push(item.id)
      })

      const weekTrendData = await axios.get(`https://api.themoviedb.org/3/trending/all/week?api_key=88c8e859d46625c472d014b2f3c995b0`)
      console.log(weekTrendData.data.results)
      this.weekTrend = weekTrendData.data.results
        this.weekTrend.map((item)=>{
        this.weekTrendID.push(item.id)
      })

    },

    methods: {
      clickToday(){
        this.todayShow = true
        this.weekShow = false
      },
      clickWeek(){
        this.weekShow = true
        this.todayShow = false
      }
    }
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
    cursor: pointer;
    font-size: 15px bold;
    height: 100%;
    display: flex;
    text-align: left;
    margin: 0px 20px 0px 20px;
  }

  .content-header ul > li {
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