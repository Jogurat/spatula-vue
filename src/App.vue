<template>
  <div id="app">
    <h1 id="ad-copy">
      Cash in your knowledge <br />with <span id="spatula">SPATULA</span>
    </h1>
    <Card v-bind:profile="searchRes"></Card>

    <div class="tab-container">
      <span class="tab" @click="clickTwitter()">Twitter</span>
      <span class="tab" @click="clickIg()">TikTok</span>
    </div>
    <!-- <transition-group name="side-fade"> -->
    <input type="text" name="" id="" v-model="username" />

    <div id="twitter" class="flex-container" v-if="!show">
      <button class="btn" @click="searchTwitter()">
        Twitter

        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="icon icon-tabler icon-tabler-tools-kitchen"
          width="30"
          height="30"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="#2c3e50"
          fill="none"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <!-- <path stroke="none" d="M0 0h24v24H0z" fill="none" /> -->
          <path d="M4 3h8l-1 9h-6z" />
          <path d="M7 18h2v3h-2z" />
          <line x1="8" y1="12" x2="8" y2="18" />
        </svg>
      </button>
    </div>
    <div id="instagram" class="flex-container" v-if="show">
      <!-- <input type="text" name="" id="" /> -->
      <button class="btn">
        TikTok

        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="icon icon-tabler icon-tabler-tools-kitchen"
          width="30"
          height="30"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="#2c3e50"
          fill="none"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <!-- <path stroke="none" d="M0 0h24v24H0z" fill="none" /> -->
          <path d="M4 3h8l-1 9h-6z" />
          <path d="M7 18h2v3h-2z" />
          <line x1="8" y1="12" x2="8" y2="18" />
        </svg>
      </button>
    </div>

    <div class="circle"></div>
    <!-- </transition-group> -->
  </div>
</template>

<script>
import axios from "axios";
import Card from "./components/Card";

export default {
  name: "App",
  components: {
    Card,
  },
  methods: {
    clickIg() {
      this.show = true;
    },
    clickTwitter() {
      this.show = false;
    },
    async searchTwitter() {
      const { data } = await axios.get(
        `http://188.166.85.199:1313/twitter/${this.username}`
      );
      console.log(data);
      this.searchRes = data;
      this.numFollowers = data["FollowersCount"];
    },
  },
  data() {
    return {
      show: false,
      username: "",
      numFollowers: 0,
      searchRes: {},
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Nunito:wght@200;400;600;900&display=swap");

#app {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100vh;
  justify-content: center;
  align-items: center;
  font-weight: 200;
  font-family: "Nunito", sans-serif;
}

.flex-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.tab {
  padding: 10px;
}

#instagram {
  /* margin-right: 100%; */
}

.slide-fade-enter-active {
  transition: all 0.3s ease;
}
.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}

#spatula {
  color: #8d83f7;
  /* font-weight: 700; */
}

#ad-copy {
  text-align: center;
  font-weight: 600;
  font-size: 4rem;
}

.circle {
  height: 500px;
  width: 500px;
  background-color: #f0edfc;
  border-radius: 50%;
  z-index: -1;
  position: fixed;
  margin-left: -500px;
  margin-top: -300px;
}

button {
  background-color: #83f7c7;
  border: none;
  outline: none;
  padding: 10px;
  border-radius: 8px;
  cursor: pointer;
  color: #373362;
  font-weight: 600;
  margin-top: 10px;
  font-size: 1rem;
}

.btn {
  display: flex;
  /* justify-content: center; */
  align-items: center;
  gap: 10px;
  padding-left: 30px;
  padding-right: 23px;
  -webkit-box-shadow: -1px 5px 15px 5px #e3e0f1;
  box-shadow: -1px 5px 15px 5px #e3e0f1;
}

.btn:hover {
  -webkit-box-shadow: -1px 5px 15px 5px #d9d6e6;
  box-shadow: -1px 5px 15px 5px #d9d6e6;
  cursor: pointer;
  transform: scale(1.01);
}

@media only screen and (max-width: 600px) {
  .circle {
    height: 40vh;
    width: 40vh;
    top: 50vh;
    margin-left: -30px;
  }
  #ad-copy {
    font-size: 2.5rem;
  }
}
</style>
