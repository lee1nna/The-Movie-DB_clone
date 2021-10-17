<template>
    <div>
        <Header/>
        <div>인기있는 tv 상세페이지</div>
        <div>{{popularTvInfo}}</div>
        <Footer/>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
            popularTvInfo: [],
        }
    },

    created() {
        console.log(this.$fetch)
    },

    async fetch({params}) {
      const { data } = await axios.get(`https://api.themoviedb.org/3/tv/${params.id}?api_key=88c8e859d46625c472d014b2f3c995b0&language=en-US`)
      this.popularTvInfo = data
    //   console.log(this.popularTvInfo)
    }
}
</script>