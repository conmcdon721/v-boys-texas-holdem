<template>
  <div id="app">
    <Dealer @deal-cards="dealCards()" />
    <Hands :playerHands="playerHands" />
  </div>
</template>

<script>
import Dealer from "./components/Dealer.vue";
import Hands from "./components/Hands.vue";

// Sockets io

export default {
  name: "App",

  components: {
    Dealer,
    Hands,
  },

  data() {
    return {
      deck: [
        { suit: "spades", value: [1, 14], id: 1 },
        { suit: "spades", value: 2, id: 2 },
        { suit: "spades", value: 3, id: 3 },
        { suit: "spades", value: 4, id: 4 },
        { suit: "spades", value: 5, id: 5 },
        { suit: "spades", value: 6, id: 6 },
        { suit: "spades", value: 7, id: 7 },
        { suit: "spades", value: 8, id: 8 },
        { suit: "spades", value: 9, id: 9 },
        { suit: "spades", value: 10, id: 10 },
        { suit: "spades", value: 11, id: 11 },
        { suit: "spades", value: 12, id: 12 },
        { suit: "spades", value: 13, id: 13 },
        { suit: "hearts", value: [1, 14], id: 14 },
        { suit: "hearts", value: 2, id: 15 },
        { suit: "hearts", value: 3, id: 16 },
        { suit: "hearts", value: 4, id: 17 },
        { suit: "hearts", value: 5, id: 18 },
        { suit: "hearts", value: 6, id: 19 },
        { suit: "hearts", value: 7, id: 20 },
        { suit: "hearts", value: 8, id: 21 },
        { suit: "hearts", value: 9, id: 22 },
        { suit: "hearts", value: 10, id: 23 },
        { suit: "hearts", value: 11, id: 24 },
        { suit: "hearts", value: 12, id: 25 },
        { suit: "hearts", value: 13, id: 26 },
        { suit: "clubs", value: [1, 14], id: 27 },
        { suit: "clubs", value: 2, id: 28 },
        { suit: "clubs", value: 3, id: 29 },
        { suit: "clubs", value: 4, id: 30 },
        { suit: "clubs", value: 5, id: 31 },
        { suit: "clubs", value: 6, id: 32 },
        { suit: "clubs", value: 7, id: 33 },
        { suit: "clubs", value: 8, id: 34 },
        { suit: "clubs", value: 9, id: 35 },
        { suit: "clubs", value: 10, id: 36 },
        { suit: "clubs", value: 11, id: 37 },
        { suit: "clubs", value: 12, id: 38 },
        { suit: "clubs", value: 13, id: 39 },
        { suit: "diamonds", value: [1, 14], id: 40 },
        { suit: "diamonds", value: 2, id: 41 },
        { suit: "diamonds", value: 3, id: 42 },
        { suit: "diamonds", value: 4, id: 43 },
        { suit: "diamonds", value: 5, id: 44 },
        { suit: "diamonds", value: 6, id: 45 },
        { suit: "diamonds", value: 7, id: 46 },
        { suit: "diamonds", value: 8, id: 47 },
        { suit: "diamonds", value: 9, id: 48 },
        { suit: "diamonds", value: 10, id: 49 },
        { suit: "diamonds", value: 11, id: 50 },
        { suit: "diamonds", value: 12, id: 51 },
        { suit: "diamonds", value: 13, id: 52 },
      ],

      playerHands: [
        {
          player: 1,
          hand: [],
        },
        {
          player: 2,
          hand: [],
        },
        {
          player: 3,
          hand: [],
        },
        {
          player: 4,
          hand: [],
        },
        {
          player: 5,
          hand: [],
        },
        {
          player: 6,
          hand: [],
        },
        {
          player: 7,
          hand: [],
        },
        {
          player: 8,
          hand: [],
        },
        {
          player: 9,
          hand: [],
        },
      ],
    };
  },

  methods: {
    dealCards() {
      this.playerHands.forEach((player) => {
        player.hand = [];

        if (this.deck.length === 0) {
          this.deck = [
            { suit: "spades", value: [1, 14], id: 1 },
            { suit: "spades", value: 2, id: 2 },
            { suit: "spades", value: 3, id: 3 },
            { suit: "spades", value: 4, id: 4 },
            { suit: "spades", value: 5, id: 5 },
            { suit: "spades", value: 6, id: 6 },
            { suit: "spades", value: 7, id: 7 },
            { suit: "spades", value: 8, id: 8 },
            { suit: "spades", value: 9, id: 9 },
            { suit: "spades", value: 10, id: 10 },
            { suit: "spades", value: 11, id: 11 },
            { suit: "spades", value: 12, id: 12 },
            { suit: "spades", value: 13, id: 13 },
            { suit: "hearts", value: [1, 14], id: 14 },
            { suit: "hearts", value: 2, id: 15 },
            { suit: "hearts", value: 3, id: 16 },
            { suit: "hearts", value: 4, id: 17 },
            { suit: "hearts", value: 5, id: 18 },
            { suit: "hearts", value: 6, id: 19 },
            { suit: "hearts", value: 7, id: 20 },
            { suit: "hearts", value: 8, id: 21 },
            { suit: "hearts", value: 9, id: 22 },
            { suit: "hearts", value: 10, id: 23 },
            { suit: "hearts", value: 11, id: 24 },
            { suit: "hearts", value: 12, id: 25 },
            { suit: "hearts", value: 13, id: 26 },
            { suit: "clubs", value: [1, 14], id: 27 },
            { suit: "clubs", value: 2, id: 28 },
            { suit: "clubs", value: 3, id: 29 },
            { suit: "clubs", value: 4, id: 30 },
            { suit: "clubs", value: 5, id: 31 },
            { suit: "clubs", value: 6, id: 32 },
            { suit: "clubs", value: 7, id: 33 },
            { suit: "clubs", value: 8, id: 34 },
            { suit: "clubs", value: 9, id: 35 },
            { suit: "clubs", value: 10, id: 36 },
            { suit: "clubs", value: 11, id: 37 },
            { suit: "clubs", value: 12, id: 38 },
            { suit: "clubs", value: 13, id: 39 },
            { suit: "diamonds", value: [1, 14], id: 40 },
            { suit: "diamonds", value: 2, id: 41 },
            { suit: "diamonds", value: 3, id: 42 },
            { suit: "diamonds", value: 4, id: 43 },
            { suit: "diamonds", value: 5, id: 44 },
            { suit: "diamonds", value: 6, id: 45 },
            { suit: "diamonds", value: 7, id: 46 },
            { suit: "diamonds", value: 8, id: 47 },
            { suit: "diamonds", value: 9, id: 48 },
            { suit: "diamonds", value: 10, id: 49 },
            { suit: "diamonds", value: 11, id: 50 },
            { suit: "diamonds", value: 12, id: 51 },
            { suit: "diamonds", value: 13, id: 52 },
          ];
        }

        let randomCard1 =
          this.deck[Math.floor(Math.random() * this.deck.length)];
        player.hand.push(randomCard1);
        this.deck.splice(this.deck.indexOf(randomCard1), 1);

        if (this.deck.length === 0) {
          this.deck = [
            { suit: "spades", value: [1, 14], id: 1 },
            { suit: "spades", value: 2, id: 2 },
            { suit: "spades", value: 3, id: 3 },
            { suit: "spades", value: 4, id: 4 },
            { suit: "spades", value: 5, id: 5 },
            { suit: "spades", value: 6, id: 6 },
            { suit: "spades", value: 7, id: 7 },
            { suit: "spades", value: 8, id: 8 },
            { suit: "spades", value: 9, id: 9 },
            { suit: "spades", value: 10, id: 10 },
            { suit: "spades", value: 11, id: 11 },
            { suit: "spades", value: 12, id: 12 },
            { suit: "spades", value: 13, id: 13 },
            { suit: "hearts", value: [1, 14], id: 14 },
            { suit: "hearts", value: 2, id: 15 },
            { suit: "hearts", value: 3, id: 16 },
            { suit: "hearts", value: 4, id: 17 },
            { suit: "hearts", value: 5, id: 18 },
            { suit: "hearts", value: 6, id: 19 },
            { suit: "hearts", value: 7, id: 20 },
            { suit: "hearts", value: 8, id: 21 },
            { suit: "hearts", value: 9, id: 22 },
            { suit: "hearts", value: 10, id: 23 },
            { suit: "hearts", value: 11, id: 24 },
            { suit: "hearts", value: 12, id: 25 },
            { suit: "hearts", value: 13, id: 26 },
            { suit: "clubs", value: [1, 14], id: 27 },
            { suit: "clubs", value: 2, id: 28 },
            { suit: "clubs", value: 3, id: 29 },
            { suit: "clubs", value: 4, id: 30 },
            { suit: "clubs", value: 5, id: 31 },
            { suit: "clubs", value: 6, id: 32 },
            { suit: "clubs", value: 7, id: 33 },
            { suit: "clubs", value: 8, id: 34 },
            { suit: "clubs", value: 9, id: 35 },
            { suit: "clubs", value: 10, id: 36 },
            { suit: "clubs", value: 11, id: 37 },
            { suit: "clubs", value: 12, id: 38 },
            { suit: "clubs", value: 13, id: 39 },
            { suit: "diamonds", value: [1, 14], id: 40 },
            { suit: "diamonds", value: 2, id: 41 },
            { suit: "diamonds", value: 3, id: 42 },
            { suit: "diamonds", value: 4, id: 43 },
            { suit: "diamonds", value: 5, id: 44 },
            { suit: "diamonds", value: 6, id: 45 },
            { suit: "diamonds", value: 7, id: 46 },
            { suit: "diamonds", value: 8, id: 47 },
            { suit: "diamonds", value: 9, id: 48 },
            { suit: "diamonds", value: 10, id: 49 },
            { suit: "diamonds", value: 11, id: 50 },
            { suit: "diamonds", value: 12, id: 51 },
            { suit: "diamonds", value: 13, id: 52 },
          ];
        }

        let randomCard2 =
          this.deck[Math.floor(Math.random() * this.deck.length)];
        player.hand.push(randomCard2);
        this.deck.splice(this.deck.indexOf(randomCard2), 1);
      });
    },

    sendMessage: function (message) {
      console.log(this.connection);
      this.connection.send(message);
    },
  },

  created: function () {
    console.log("Starting connection to WebSocket Server");
    this.connection = new WebSocket("wss://echo.websocket.org");

    this.connection.onopen = function (event) {
      console.log(event);
      console.log("Successfully connected to the echo WebSocket Server");
    };

    this.connection.onmessage = function (event) {
      console.log(event);
    };
  },
};
</script>

<style></style>
