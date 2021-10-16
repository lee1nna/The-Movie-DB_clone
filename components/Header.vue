<template>
    <div class="page_wrap">
  <header>
    <div class="nav_bar">
      <img src="https://www.themoviedb.org/assets/2/v4/logos/v2/blue_short-8e7b30f73a4020692ccca9c88bafe5dcb6f8a62a4c6bc55cd9ba82bb2cd95f6c.svg" alt="">
			<div id="left_nav">
				<ul>
					<li><a href="#">영화</a></li>
					<li><a href="">TV프로그램</a></li>
					<li><a href="">인물</a></li>
					<li><a href="">More</a></li>
				</ul>
			</div>
      <div id="right_nav">
				<ul>
					<li><a href="#">+</a></li>
					<li><a href="">KO</a></li>
					<li><a href="">종</a></li>
					<li><a href="">프로필</a></li>
          <li><a href="">검색</a></li>
				</ul>
			</div>
    </div>
  </header>
</div>
</template>

<style>
  header{
    background-color: #0d253f;
    width: 100%;
    height: 64px;
  }

  ul{
    list-style: none;
  }

  a{
    text-decoration: none;
    outline: none;
  }

  .nav_bar{
    width: 1300px;
    height: 40px;
    margin: 0 auto;
    padding: 30px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .nav_bar > img {
    /* margin-left: 20px 20px 20px 20px; */
    height: 20px;
  }

  .nav_bar ul {
    margin: 0;
    width: 100%;
    height: 100%;
    display: flex;
  }

  .nav_bar ul > li {
    font-size: 15px bold;
    height: 100%;
    display: flex;
    align-items: center;
    text-align: left;
    margin: 0px 20px 0px 20px;
  }

  .nav_bar ul > li a {
    text-decoration: none;
    color: aliceblue;
  }

  .nav_bar > #left_nav{
    position: relative;
    right: 150px;
    height: 100%;
  }

  .nav_bar > #right_nav{
    height: 100%;
  }
</style>