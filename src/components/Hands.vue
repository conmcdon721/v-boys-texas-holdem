<template>
  <div>
    <h1 v-for="player in playerHands" :key="player.player">
      <img :src="getCardImage(player.hand[0].id)" />
      <img :src="getCardImage(player.hand[1].id)" />
    </h1>
  </div>
</template>

<script>
export default {
  name: "Hands",
  props: {
    playerHands: Array,
  },
  methods: {
    getCardImage(card) {
      let cardImage = require.context("../assets/", false, /\.png$/);
      return cardImage(`./${card}.png`);
    },
  },
};
</script>

<style>
img {
  width: 5%;
}
</style>
