<template>
  <div>
    <button @click="dealCards">Deal</button>
  </div>
</template>

<script>
export default {
  name: "Dealer",
  methods: {
    dealCards() {
      this.$emit("deal-cards");
    },
  },
};
</script>

<style></style>
