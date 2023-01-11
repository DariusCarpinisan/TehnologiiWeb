<script>
import axios from "axios";
export default {
  name: "Stats",
  data() {
    return {
      searchText: "",
      setSearchText: "",
      summonerData: [],
      summonerName: "",
      summonerLevel: "",
      summonerpuuID: "",
      summonerMatchesID: [],
      matches: [],
      matchone: "",
    };
  },
  methods: {
    fetchSummoner() {
      const Url = `https://na1.api.riotgames.com/lol/summoner/v4/summoners/by-name/${this.setSearchText}?api_key=RGAPI-f3c60d6d-9cff-4277-9ece-c0e04670886f`;
      fetch(Url)
        .then((response) => response.json())
        .then((data) => {
          this.summonerData = data;
          this.summonerName = data.name;
          this.summonerLevel = data.summonerLevel;
          this.summonerpuuID = data.puuid;
          console.log(data);
        });
    },

    fetchImage() {
      const Url = `https://ddragon.leagueoflegends.com/cdn/11.6.1/img/profileicon/${this.summonerData.profileIconId}.png`;
      fetch(Url)
        .then((response) => response.json())
        .then((data) => {
          this.summonerData = data;
        });
    },

    fetchMatchID() {
      const Url = `https://americas.api.riotgames.com/lol/match/v5/matches/by-puuid/${this.summonerpuuID}/ids?start=0&count=20&api_key=RGAPI-f3c60d6d-9cff-4277-9ece-c0e04670886f`;
      fetch(Url)
        .then((response) => response.json())
        .then((data) => {
          this.summonerMatchesID = data;
          console.log(this.summonerMatchesID);
        });
    },
    fetchMatches(ids) {
      axios
        .all(
          ids.map((id) =>
            axios.get(
              `https://americas.api.riotgames.com/lol/match/v5/matches/${id}?api_key=RGAPI-f3c60d6d-9cff-4277-9ece-c0e04670886f`
            )
          )
        )
        .then(
          axios.spread((...responses) => {
            this.matches = responses;
            console.log(this.matches);
          })
        );
    },
  },
};
</script>

<template>
  <div class="Welcome">Summoner Stats</div>
  <img
    class="logo"
    src="https://upload.wikimedia.org/wikipedia/fr/7/7c/Riot_Games_Logo.png"
    alt="riotgameslogo"
  />
  <div class="searchbox">
    <input
      type="text"
      class="search-bar"
      placeholder="Search..."
      v-model="setSearchText"
    />

    <button class="search-button" @click="fetchSummoner">Search</button>
    <button class="search-button1" @click="fetchMatchID">MatchID</button>
    <button class="search-button2" @click="fetchMatches(summonerMatchesID)">
      Matches
    </button>

    <div class="name" v-if="summonerName">
      {{ summonerName }}
    </div>

    <div class="profileIcon" v-if="summonerName">
      <img
        width="100"
        height="100"
        :src="`https://ddragon.leagueoflegends.com/cdn/11.6.1/img/profileicon/${this.summonerData.profileIconId}.png`"
        alt="profile icon"
      />
      <div class="level" v-if="summonerLevel">
        <p>Level:</p>
        {{ summonerLevel }}
      </div>
    </div>
  </div>
  <div class="matches" v-if="matches.length > 0">
    <div v-for="(match, index) in matches" :key="match.data.info.gameId">
      GameMode:{{ match.data.info.gameMode }}
      <div></div>
      Time:{{ match.data.info.gameDuration % 60 }} MINUTES
      <div
        v-for="(participant, index) in match.data.info.participants"
        :key="participant.puuid"
      >
        <div class="summonername" v-if="summonerName">
          {{ participant.summonerName }}
        </div>

        <img
          width="50"
          height="50"
          :src="`https://ddragon.leagueoflegends.com/cdn/11.6.1/img/profileicon/${participant.profileIcon}.png`"
          alt="icon"
        />

        SummonerLevel: {{ participant.summonerLevel }} | K/D/A:
        {{ participant.kills }} / {{ participant.deaths }} /
        {{ participant.assists }}
        <div></div>

        <img
          width="50"
          height="50"
          :src="`https://ddragon.leagueoflegends.com/cdn/11.6.1/img/champion/${participant.championName}.png`"
          alt="icon"
        />

        {{ participant.championName }} | Lane: {{ participant.lane }}
        <div v-if="participant.win">
          <p>Winner</p>
        </div>
        <div v-else>
          <p>Lose</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.matches {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  align-items: center;
  font-family: copperplate gothic light;
  font-size: 20px;
  color: lightblue;
  border-radius: 10px;
  padding: 10px;
  margin: 10px;
  background-color: rgba(100, 132, 160, 0.5);
}
.summonername {
  font-size: 20px;
  font-weight: bold;
  font-family: copperplate gothic light;
  color: aqua;
}

.searchbox .search-bar {
  width: 150px;
  height: 30px;
  border-radius: 10px;
  border: none;
  padding: 10px;
  font-size: 20px;
  font-weight: bold;
  font-family: "Brush Script MT", "Brush Script Std", cursive;
  text-align: center;
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
}

.level {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: flex-end;
  font-size: 20px;
  font-weight: bold;
  font-family: "Brush Script MT", "Brush Script Std", cursive;
  color: white;
}
.search-button {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: lightblue;
  border-radius: 10px;
  border: none;
  padding: 10px 20px;
  text-align: center;
  transform: none;
  font-size: 15px;
  display: inline-block;
  right: 105px;
  top: 3px;
  cursor: pointer;
  outline: none;
  font-family: copperplate gothic light;
}
.search-button:hover {
  background-color: rgb(0, 191, 255);
  color: white;
}
.search-button:active {
  background-color: rgb(0, 191, 255);
  color: white;
}
.search-button1 {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: lightblue;
  border-radius: 10px;
  border: none;
  cursor: pointer;
  outline: none;
  padding: 10px 20px;
  text-align: center;
  transform: none;
  font-size: 15px;
  display: inline-block;
  top: -33px;
  font-family: copperplate gothic light;
}
.search-button1:hover {
  background-color: rgb(0, 191, 255);
  color: white;
}
.search-button1:active {
  background-color: rgb(0, 191, 255);
  color: white;
}
.search-button2 {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: lightblue;
  border-radius: 10px;
  border: none;
  padding: 10px 20px;
  text-align: center;
  transform: none;
  cursor: pointer;
  outline: none;
  display: inline-block;
  left: 110px;
  top: -68px;
  font-size: 15px;
  font-family: copperplate gothic light;
}
.search-button2:hover {
  background-color: rgb(0, 191, 255);
  color: white;
}
.search-button2:active {
  background-color: rgb(0, 191, 255);
  color: white;
}
.Welcome {
  font-size: 40px;
  font-weight: bold;
  font-family: copperplate gothic light;
  text-shadow: 5px 2px 4px #000000;
  color: rgb(0, 191, 255);
}

.searchbox {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.logo {
  position: absolute;
  top: 0%;
  left: 0%;
  width: 90px;
  height: 45px;
  margin: auto;
}
.name {
  font-size: 50px;
  top: -80px;
  font-family: "Brush Script MT", "Brush Script Std", cursive;
  text-shadow: 2px 2px 4px #000000;
  color: rgb(0, 191, 255);
}

.profileIcon {
  border-radius: 10%;
  top: -80px;
  object-fit: cover;
  overflow: hidden;
}

.nav {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  height: 50px;
  width: 100%;
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  border-radius: 10px;
  border: none;
  background-color: rgba(22, 72, 116, 0.5);
}

.home {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgb(76, 175, 208);
  border-radius: 10px;
  border: none;
  padding: 10px 30px;
  text-align: center;
  transform: none;
  font-size: 16px;
  display: inline-block;
  cursor: pointer;
  transition: all 0.5s;
  top: 0;

  font-size: 20px;
  font-family: "Brush Script MT", "Brush Script Std", cursive;
}
.home span {
  cursor: pointer;
  display: inline-block;
  position: relative;
  transition: 0.5s;
}
.home span:after {
  content: "\00bb";
  position: absolute;
  opacity: 0;
  top: 0;
  right: -20px;
  transition: 0.5s;
}
.home:hover span {
  padding-right: 25px;
}

.home:hover span:after {
  opacity: 1;
  right: 0;
}

.stats {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgb(76, 175, 208);
  border-radius: 10px;
  border: none;
  padding: 10px 30px;
  text-align: center;
  transform: none;
  font-size: 16px;
  display: inline-block;
  cursor: pointer;
  transition: all 0.5s;
  top: 0;

  font-size: 20px;
  font-family: "Brush Script MT", "Brush Script Std", cursive;
}

.stats span {
  cursor: pointer;
  display: inline-block;
  position: relative;
  transition: 0.5s;
}

.stats span:after {
  content: "\00bb";
  position: absolute;
  opacity: 0;
  top: 0;
  right: -20px;
  transition: 0.5s;
}

.stats:hover span {
  padding-right: 25px;
}

.stats:hover span:after {
  opacity: 1;
  right: 0;
}

.about {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgb(76, 175, 208);
  border-radius: 10px;
  border: none;
  padding: 10px 30px;
  text-align: center;
  transform: none;
  font-size: 16px;
  display: inline-block;
  cursor: pointer;
  transition: all 0.5s;
  top: 0;
  font-size: 20px;
  font-family: "Brush Script MT", "Brush Script Std", cursive;
}

.about span {
  cursor: pointer;
  display: inline-block;
  position: relative;
  transition: 0.5s;
}

.about span:after {
  content: "\00bb";
  position: absolute;
  opacity: 0;
  top: 0;
  right: -20px;
  transition: 0.5s;
}

.about:hover span {
  padding-right: 25px;
}

.about:hover span:after {
  opacity: 1;
  right: 0;
}
</style>
