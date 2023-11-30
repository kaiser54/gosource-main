<template>
  <div>
    <DynamicInput v-model="firstName" type="number" class="inputmee" />
    <DynamicButtonNav
      class="nav-button"
      buttonText="click me"
      url="/"
      :isLoading="true"
    />
    <DynamicButtonMain
      class="nav-button"
      buttonText="click me"
      size="large"
      type="primary"
      :isLoading="true"
    />
    <WaitlistCard
      v-for="(data, index) in waitlistData"
      :key="index"
      :data="data"
      :selectedItem="selectedItem"
      @selectEvent="selectEvent($event)"
    />
    <DynamicButtonNav buttonText="click me please" url="" />
    <p>{{ firstName }}</p>
    <Account name="Agboola t." />
  </div>
</template>

<script setup>
import { ref } from "vue";

const firstName = ref("")

const waitlistData = ref([
  {
    title: "GoSource for Business",
    snippet:
      "Get access to buy on credit, instant invoice, fast payments and 24hours delivery",
    value: "business",
    img:  "/images/business.png",
  },
  {
    title: "GoSource for Individual",
    snippet:
      "Buy your food items with discounts, lesser prices and get them in 24hours",
    value: "individual",
    img:  "/images/individual.png",
  },
]);

const selectedItem = ref("");
const selectEvent = (e) => {
  selectedItem.value = e;
};
</script>

<style scoped>
</style>
