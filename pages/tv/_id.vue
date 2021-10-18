<template>
    <div>
        <Header/>
        <div id="detail-section">
            <div class="left">
                <img :src="'https://image.tmdb.org/t/p/w200'+tvInfo.poster_path">
            </div>
            <div class="right">
                <h1>{{tvInfo.name}}</h1>
                <h6>개요</h6>
                <h2>{{tvInfo.overview}}</h2>
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
      return axios.get(`https://api.themoviedb.org/3/tv/${params.id}?api_key=88c8e859d46625c472d014b2f3c995b0&language=en-US`)
      .then((res)=>{
        //   console.log(res.data)
          return {
              tvInfo: res.data
          }
      })
    }
}
</script>