<template>
    <div class="page_wrap">
  <footer>
    <div class="footer-box">
      <img src="https://www.themoviedb.org/assets/2/v4/logos/v2/blue_square_2-d537fb228cf3ded904ef09b136fe3fec72548ebc1fea3fbbd1ad9e36364db38b.svg" alt="">
			<div id="box1">
				<ul>
					<li>THE BASICS</li>
					<li>TMDb에 대해 문의하기</li>
					<li>Support Forums API</li>
					<li>System status</li>
				</ul>
			</div>
            <div id="box2">
				<ul>
					<li>참여하기</li>
					<li>기여 지침서</li>
					<li>타사 응용 프로그램</li>
					<li>새 영화 추가</li>
                    <li>새 TV 프로그램 추가</li>
				</ul>
			</div>
            <div id="box3">
				<ul>
					<li>커뮤니티</li>
					<li>가이드라인</li>
					<li>토론 내역</li>
					<li>기여 랭킹</li>
                    <li>Twitter</li>
				</ul>
			</div>
            <div id="box4">
				<ul>
					<li>법적 사항</li>
					<li>서비스 이용약관</li>
					<li>API Terms of Use</li>
					<li>개인정보약관</li>
				</ul>
			</div>
    </div>
  </footer>
</div>
</template>

<style>
  footer{
    background-color: #0d253f;
    width: 100%;
    height: 300px;
    margin: 0 auto;
    padding: 30px;
    display: flex;
    align-items: center;
  }
  
  .footer-box{
      margin: auto;
  }

  .footer-box img{
      position: relative;
      bottom: 30px;
      width: 150px;
  }

  .footer-box div{
    position: relative;
    top: 15px;
    left: 30px;
    display: inline-block;
  }

  ul{
    list-style: none;
    font-size: 15pt;
  }

  .footer-box div li {
    color: aliceblue;
    height: 100%;
    display: flex;
    margin: 0px 20px 0px 20px;
  }

  #box2 {
      top: 40px;
  }

  #box3 {
      top: 40px;
  }
</style>