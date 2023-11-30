<template>
  <div>
    <WaitlistWrap
      :data="waitlistData"
      :currentStep="currentStep"
      :disabled="!selectedItem"
      @clickButton="nextStep()"
    >
      <template v-slot:content>
        <div class="card wrap" v-show="currentStep === 1">
          <WaitlistCard
            v-for="(data, index) in waitlistCardData"
            :key="index"
            :data="data"
            :selectedItem="selectedItem"
            @selectEvent="selectEvent($event)"
          />
        </div>
        <div class="form wrap" v-show="currentStep === 2">
          <DynamicInput
            v-model="firstInput"
            labelText="Email address"
            type="number"
            class="inputmee"
          />
          <DynamicInput
            v-model="secondInput"
            :labelText="selectedItem + ' name'"
            type="number"
            class="inputmee"
          />
        </div>
      </template>
    </WaitlistWrap>
  </div>
</template>

<script setup>
import { ref } from "vue";

// data

const firstInput = ref("");
const secondInput = ref("");
const currentStep = ref(1);
const selectedItem = ref("");
const waitlistCardData = ref([
  {
    title: "GoSource for Business",
    snippet:
      "Get access to buy on credit, instant invoice, fast payments & 24hours delivery",
    value: "business",
    img: "/images/business.svg",
  },
  {
    title: "GoSource for Individual",
    snippet: "Buy your food items with discounts, lesser prices and get them in 24hours",
    value: "full",
    img: "/images/individual.svg",
  },
]);
const waitlistData = ref([
  {
    title: "How do you want to use GoSource?",
    snippet:
      "We procure directly from farmers and manufacturers to get you the best at unbeatable prices.",
    buttonText: "Continue",
  },
  {
    title: "Join the waitlist and we will give you access to Beta Testing",
    snippet: null,
    buttonText: "Join waitlist",
  },
]);

// methods

const selectEvent = (e) => {
  selectedItem.value = e;
};

const nextStep = () => {
  currentStep.value++;
};
</script>

<style scoped>
.wrap {
  display: flex;
  align-items: flex-start;
  width: 100%;
  gap: calc(var(--spacing-unit) * 3);
}

.card {
  max-width: 507px;
}

.form {
  flex-direction: column;
  max-width: 354px;
}


</style>
