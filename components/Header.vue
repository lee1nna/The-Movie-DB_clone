<template>
    <div class="page_wrap">
  <header>
    <div class="nav_bar">
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/89/Tmdb.new.logo.svg/1280px-Tmdb.new.logo.svg.png" alt="">
			<nav id="left_nav">
				<ul>
					<li><a href="#">영화</a></li>
					<li><a href="">TV프로그램</a></li>
					<li><a href="">인물</a></li>
					<li><a href="">More</a></li>
				</ul>
			</nav>
      <nav id="right_nav">
				<ul>
					<li><a href="#">+</a></li>
					<li><a href="">KO</a></li>
					<li><a href="">종</a></li>
					<li><a href="">프로필</a></li>
          <li><a href="">검색</a></li>
				</ul>
			</nav>
    </div>
  </header>

  <div class="content">
  </div>
</div>
</template>

<style>
  header{
    background-color: #032541;
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
    position: relative;
    /* margin: 0 auto; */
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .nav_bar > img {
    /* margin-left: 20px 20px 20px 20px; */
    height: 40px;
  }


  .nav_bar ul {
    margin: 0;
    width:100%;
    height: 100%;
    display: flex;
  }

  .nav_bar ul > li {
    font-size: 15px bold;
    height: 100%;
    display: flex;
    align-items: center;
    margin: 0px 20px 0px 20px;
  }

  .nav_bar ul > li a {
    color: aliceblue;
  }

  .nav_bar > #left_nav{
    width: 300px;
    height: 100%;
  }

  .nav_bar > #right_nav{
    width: 400px;
    height: 100%;
  }
</style>