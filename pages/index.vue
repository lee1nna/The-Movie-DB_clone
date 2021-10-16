<template>
  <div>
    <Header/>
    <div class="main">
      <img class="main-img" src="https://www.themoviedb.org/t/p/w1920_and_h600_multi_faces_filter(duotone,032541,01b4e4)/rCxdJkk5PMCWIzRWcpqIxUaWnf1.jpg" alt="">
      <div class="main-text">
        <h1>Welcome.</h1>
        <h2>Millions of movies, TV shows and people to discover. Explore now.</h2>
      </div>
    </div>
    <PopularArea/>
    <FreeToWatchArea/>
    <LatestTrailerArea/>
  </div>
</template>

<script>
export default {

  }
</script>

<style>

  .main{
    position: relative;
    text-align: center;
  }

  .main .main-text{
    position: absolute;
    color: aliceblue;
    text-align: left;
    margin:auto;
    top: 90px;
    left: 80px;
    z-index: 1;
  }

  .main-img{
    height: 100%;
    max-width: 1300px;

  }
</style>