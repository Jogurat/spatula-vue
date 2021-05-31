<template>
  <div class="card-container">
    <div class="left">
      <img
        class="avatar"
        :src="
          'https://avatars.dicebear.com/api/avataaars/' +
          profile.username +
          '.svg'
        "
        alt="random-avatar"
      />
      <p class="username">{{ profile.username }}</p>
    </div>
    <div class="right">
      <p class="stats">Followers: {{ profile.followersCount }}</p>
      <p class="stats">Posts: {{ profile.postsCount }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["profile"],
};
</script>

<style>
.card-container {
  width: 38%;
  height: 130px;
  display: flex;
  /* border: 1px solid black; */
  background-color: #83f7c7;
  border-radius: 9px;
  -webkit-box-shadow: -1px 5px 15px 5px #e3e0f1;
  box-shadow: -1px 5px 15px 5px #e3e0f1;
}

.right,
.left {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
}

.left {
  flex-direction: row;
  align-items: center;
  justify-content: space-evenly;
}

.left p {
  padding: 0;
  /* margin: 0; */
}

.right {
  justify-content: center;
}

.card-container:hover {
  -webkit-box-shadow: -1px 5px 15px 5px #d9d6e6;
  box-shadow: -1px 5px 15px 5px #d9d6e6;
  cursor: pointer;
  transform: scale(1.01);
}

.avatar {
  border-radius: 50%;
  width: 25%;
  /* margin-left: 10%; */
}

.username {
  /* margin-left: 10%; */
  color: #8d83f7;
  font-weight: 600;
  letter-spacing: 2px;
  font-size: 25px;
}

.stats {
  font-size: 20px;
  font-weight: 400;
  letter-spacing: 1px;
}
</style>