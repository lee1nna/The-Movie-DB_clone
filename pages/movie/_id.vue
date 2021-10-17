<template>
    <div>
        <Header/>
        <div>인기있는 movie 상세페이지</div>
        <div>
            <img :src="'https://image.tmdb.org/t/p/w200'+popularTvInfo.poster_path">
        </div>
        <div>
            {{popularTvInfo.overview}}
        </div>
        <div>{{popularTvInfo.name}}</div>
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
              popularTvInfo: res.data
          }
      })
    }
}
</script>