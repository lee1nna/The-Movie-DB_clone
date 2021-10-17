<template>
    <div>
        <Header/>
        <div id="detail-section">
            <div class="left">
                <img :src="'https://image.tmdb.org/t/p/w200'+movieInfo.poster_path">
            </div>
            <div class="right">
                <h1>{{movieInfo.title}}</h1>
                <h6>개요</h6>
                <h2>{{movieInfo.overview}}</h2>
            </div>
        </div>
        <Footer/>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
        }
    },

    asyncData ({params}) {
      return axios.get(`https://api.themoviedb.org/3/movie/${params.id}?api_key=88c8e859d46625c472d014b2f3c995b0&language=en-US`)
      .then((res)=>{
          console.log(res.data)
          return {
              movieInfo: res.data
          }
      })
    }
}
</script>

<style>

    #detail-section {
        margin: auto;
        max-width: 1300px;
        height: 800px;
    }

    #detail-section .left{
        position: relative;
        width: 300px;
        height: 450px;
        left: 50px;
        top: 100px; 
        float: left;
    }

    #detail-section .left img{
        width: 300px;
        height: 450px;
    }

    #detail-section .right{
        position: relative;
        right: 230px;
        top: 100px;
        width: 50%;
        float: right;
        box-sizing: border-box;
        /* background: rgb(255, 0, 0); */
    }

    #detail-section .right h1{
        font-weight: bold;
    }

    #detail-section .right h2{
        font-size: 17pt;
        position: relative;
        top: 150px;
    }
    #detail-section .right h6{
        font-size: 18pt;
        position: relative;
        right: 1px;
        top: 140px;
    }
</style>