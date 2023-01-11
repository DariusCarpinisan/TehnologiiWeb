<script>
export default {
  name: "Home",
  data() {
    return {};
  },
  methods: {},
};
</script>

<template>


  <div class="ch1">2022 World Championship [Worlds 2022] 29.09.2022 - 06.11.2022</div>
  <div class="ch2">2022 Mid-Season Invitational [MSI 2022] 03.05.2022 - 08.05.2022</div>
  <div class="ch3">2022 League of Legends Championship Series [LCS 2022] 01.01.2022 - 31.12.2022</div>
  <div class="ch4">2022 League of Legends European Championship [LEC 2022] 01.01.2022 - 31.12.2022</div>
  <div class="ch5">Season 2023 Kickoff | The Madness is the Hype</div>
  <div class="ch6">Vote For the Cause You want to Support</div>
  <div class="ch7">Now Streaming on Riot Mobile</div>
  <div class="ch8">Welcome to RIOT GAMES Statistic</div>
  <section class="wrapper">
  <div class="top">Home Page</div>
  <div class="bottom" aria-hidden="true">Home Page</div>
</section>
<div class="faker">NEWS</div>
<section class="test">
  <div class="isolate">
    <div class="noise">••• Championship Tournaments •••</div>
    <div class="overlay"></div>
  </div>
</section>
  <img
    class="logo"
    src="https://upload.wikimedia.org/wikipedia/fr/7/7c/Riot_Games_Logo.png"
    alt="riotgameslogo"
  />
  <img
    class="championship"
    src="https://www.esports.net/wp-content/uploads/2020/01/na-lcs-north-america-league-of-legends-championship-series.jpg"
    alt="riotgameschampionship"
  />
  <img class="championship2" src="https://www.riotgames.com/darkroom/1000/4ff10e1371412d5f42fd884043b94e24:7c9ac71d2992d3edce7faae1d9ae7258/sn23-hype-film-banner-textless.jpg" alt="riotgameschampionship2" />
  <img class="championship3" src="https://www.riotgames.com/darkroom/1000/b44009806fcf1e2a03003957cd3de777:ffcc762769ad5d6dd01745eccce84ec0/karma-charity-articlebanner.png" alt="riotgameschampionship3" />
  <img class="championship4" src="https://www.riotgames.com/darkroom/1000/c99180dd9326186d22ab2044e3190a85:f2c961f0caa689fed9c6795d59c07890/rg-com-lol-article-t1-cluttered-decluttered.jpg" alt="riotgameschampionship4" />
</template>

<style>
.faker{
  color: rgb(255, 255, 255);
  font-size: 16px;
  text-shadow: 4px 2px 4px #000000;
  position: absolute;
  align-items: center;
  justify-content: center;
  top: 55px;
  left: 90%;
  font-weight: bold;
  font-family: copperplate gothic light;
  background-color: red;
  width: 57px;
}
.ch5{
  color: rgb(255, 255, 255);
  font-size: 15px;
  text-shadow: 4px 2px 4px #000000;
  position: absolute;
 
  top: 255px;
  left: 80%;
 
  font-family: copperplate gothic light;
  
 
}
.ch6{
  color: rgb(255, 255, 255);
  font-size: 15px;
  text-shadow: 4px 2px 4px #000000;
  position: absolute;
  top: 485px;
  left: 80%;

  font-family: copperplate gothic light;
  
 
}
.ch7{
  color: rgb(255, 255, 255);
  font-size: 15px;
  text-shadow: 4px 2px 4px #000000;
  position: absolute; 
  top: 715px;
  left: 80%;
  font-family: copperplate gothic light;
}
.ch8{
  color: rgb(255, 255, 255);
  font-size: 12px;
  text-shadow: 4px 2px 4px #000000;
  position: absolute;
  font-weight: bold;
 
  top: 180px;
  left: 35%;
 
  font-family: copperplate gothic light;
  
 
}

.logo {
  position: absolute;
  top: 0%;
  left: 0%;
  width: 90px;
  height: 45px;
  margin: auto;
  display: block;
}

.championship {
  position: absolute;
  
  top:10%;
  left: 47px;
  width: 300px;
  height: 180px;
  margin: auto;
  display: block;
}
.championship2{
width: 300px;
left: 80%;
top: -480px;
}
.championship3{
  width: 300px;
  left: 60%;
  top: -250px;
}
.championship4{
  width: 300px;
  left: 40%;
  top: -10px;
}
.ch1{
  color: rgb(0, 191, 255);
  font-size: 12px;
  text-shadow: 2px 2px 4px #000000;
  position: absolute;
  top: 35%;
  left: 3%;
  font-weight: bold;
  font-family: copperplate gothic light;

}
.ch2{
  color: rgb(0, 191, 255);
  font-size: 12px;
  text-shadow: 2px 2px 4px #000000;
  position: absolute;
  top: 37%;
  left: 3%;
  font-weight: bold;
  font-family: copperplate gothic light;

}
.ch3{
  color: rgb(0, 191, 255);
  font-size: 12px;
  text-shadow: 2px 2px 4px #000000;
  position: absolute;
  top: 39%;
  left: 3%;
  font-weight: bold;
  font-family: copperplate gothic light;

}

.ch4{
  color: rgb(0, 191, 255);
  font-size: 12px;
  text-shadow: 2px 2px 4px #000000;
  position: absolute;
  top: 41%;
  left: 3%;
  font-weight: bold;
  font-family: copperplate gothic light;

}
:root {
  --text-color: hsl(213, 100%, 50%);
}
body {
  margin: 0;
}
.wrapper {
  display: grid;
  place-content: center;
  background-color: var(--background-color);
  
  font-family: "Brush Script MT", cursive;
  font-size: 8vw;
  
  
  color: var(--text-color);
}

.wrapper > div {
  grid-area: 1/1/-1/-1;
}
.top {
  clip-path: polygon(0% 0%, 100% 0%, 100% 48%, 0% 58%);
}
.bottom {
  clip-path: polygon(0% 60%, 100% 50%, 100% 100%, 0% 100%);
  color: transparent;
  background: -webkit-linear-gradient(177deg, rgb(242, 2, 2) 53%, var(--text-color) 65%);
  background: linear-gradient(177deg, rgb(0, 26, 156) 53%, var(--text-color) 65%);
  background-clip: text;
  -webkit-background-clip: text;
  transform: translateX(-0.02em);
}

/*  */


section.test {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 400px;
  height: 310px;
  animation-duration: 2s;
  animation-name: cube-rotate;
  animation-iteration-count: infinite;
  animation-direction: alternate;
  animation-timing-function: ease-in-out;
}


.isolate {
  isolation: isolate;
  position: absolute;
  top: 0;
  height: 100%;
  width: 100%;
}

@keyframes cube-rotate {
  from {
    transform: perspective(600px) rotate3d(0.6, 0.05, 0.2, 0deg);
  }

  to {
    transform: perspective(600px) rotate3d(0.6, 0.05, 0.2, 20deg);
  }
}

@keyframes shimmer {
  from {
    filter: contrast(190%) brightness(500%);
  }

  to {
    filter: contrast(190%) brightness(130%);
  }
}

.noise {
  top: -200px;
  width: 100%;
  height: 100%;
  padding: 8px;
  background: linear-gradient(24deg, rgba(51, 0, 255, 0.1), CornflowerBlue), url("data:image/svg+xml,%3Csvg viewBox='0 0 400 310' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.55' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E");
  background-clip: text;
  font-family:'Courier New', Courier, monospace;
  font-size: 15px;
  text-shadow: 2px 2px 4px #000000;
  text-align: center;
  -webkit-background-clip: text;
	color: transparent;
  animation-duration: 2s;
  animation-name: shimmer;
  animation-iteration-count: infinite;
  animation-direction: alternate;
}

.overlay {
  position: absolute;
  top: 0;
  width: 100%;
  height: 100%;
  mix-blend-mode: multiply;
}


@media all and (-webkit-min-device-pixel-ratio:0) and (min-resolution: .001dpcm) {
  .overlay {
    opacity: 0.6;
  }
}

</style>
