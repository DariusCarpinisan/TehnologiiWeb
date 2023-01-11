<script>
export default {
  name: "About",
  data() {
    return {};
  },
};
</script>

<template>
  <img
    class="logo"
    src="https://upload.wikimedia.org/wikipedia/fr/7/7c/Riot_Games_Logo.png"
    alt="riotgameslogo"
  />
<div></div>
<div class="welcome">About Project</div>
  <button class="btn info">CODE EXAMPLE</button>
  <div class="main">
    <div class="axios">Axios getting Matches Data by ID</div>
    fetchMatches(ids) {
      axios
        .all(
          ids.map((id) =>
            axios.get(
              `URL`
            )
          )
        )
        <div></div>
        .then(
          axios.spread((...responses) => {
            <div></div>
            this.matches = responses;
            console.log(this.matches);
          })
        );
    },
  },
  <div class="axios">Fetching Summoner</div>
  <div>fetchSummoner() {
      const Url = `URL`;
      fetch(Url)
      <div></div>
        .then((response) => response.json())
        .then((data) => {
          this.summonerData = data;
          <div></div>
          this.summonerName = data.name;
          <div></div>
          this.summonerLevel = data.summonerLevel;
          <div></div>
          this.summonerpuuID = data.puuid;
          console.log(data);
        });
    },</div>
    <div class="axios">Some CSS</div>
    <div>
.wrapper {<div></div>
  display: grid;<div></div>
  place-content: center;<div></div>
  background-color: var(--background-color);<div></div>
  font-family: "Brush Script MT", cursive;<div></div>
  font-size: 8vw;<div></div>
  color: var(--text-color);<div></div>
}

.wrapper > div {<div></div>
  grid-area: 1/1/-1/-1;<div></div>
}<div></div>
.top {<div></div>
  clip-path: polygon(0% 0%, 100% 0%, 100% 48%, 0% 58%);
}<div></div>
.bottom {<div></div>
  clip-path: polygon(0% 60%, 100% 50%, 100% 100%, 0% 100%);<div></div>
  color: transparent;<div></div>
  background: -webkit-linear-gradient(177deg, rgb(242, 2, 2) 53%, var(--text-color) 65%);<div></div>
  background: linear-gradient(177deg, rgb(0, 26, 156) 53%, var(--text-color) 65%);<div></div>
  background-clip: text;<div></div>
  -webkit-background-clip: text;<div></div>
  transform: translateX(-0.02em);</div>
  </div>
  

</template>

<style>
.welcome{
  color: rgb(255, 255, 255);
  font-size: 16px;
  text-shadow: 4px 2px 4px #000000;
  position: absolute;
font-size: 40px;
color: rgb(0, 191, 255);
  font-weight: bold;
  font-family: copperplate gothic light;

  width: 57px;
}
.axios{
  color:#2196F3;
  font-family: copperplate gothic light;
  font-size: 25px;
  left: 9px;
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
.btn {
  border: none; 
  color: white;
  padding: 14px 28px;
  cursor: pointer; 
  left: 1px;
  top: 160px;
}
.info {background-color: #2196F3;}
.info:hover {background: #0b7dda;}


.main{
top: 150px;
background: #f5f5f5;
border: 1px solid #e8e8e8;
border-radius: 3px;
font-family: monospace;
font-size: 14px;
line-height: 1.5;
margin: 1em 0;
overflow: auto;
padding: 1em;
white-space: pre;
word-spacing: normal;
width: 50%;
height: 250px;
}
</style>
