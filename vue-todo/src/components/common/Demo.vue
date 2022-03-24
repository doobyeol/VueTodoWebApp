<template>
  <div id="root">
    <p>orginalPrice</p>
    100
    <p>doublePrice</p>
    200
    <p>triplePrice</p>
    300
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  computed: {
    ...mapGetters([orginalPrice, doublePrice, triplePrice]),
    // orginalPrice() {
    //   return this.$store.getters.orginalPrice;
    // },
    // doublePrice() {
    //   return this.$store.getters.doublePrice;
    // },
    // triplePrice() {
    //   return this.$store.getters.triplePrice;
    // },
  },
};
</script>

<style>
</style>