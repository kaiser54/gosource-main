<template>
  <WaitlistLayout>
    <WaitlistWrap
      v-if="currentStep < 3"
      :data="waitlistData"
      :currentStep="currentStep"
      :disabled="!selectedItem"
      @clickButton="nextStep()"
    >
      <template v-slot:content>
        <transition appear mode="out-in">
          <div class="card wrap" v-if="currentStep === 1">
            <WaitlistCard
              v-for="(data, index) in waitlistCardData"
              :key="index"
              :data="data"
              :selectedItem="selectedItem"
              @selectEvent="selectEvent($event)"
            />
          </div>
        </transition>
        <transition appear mode="out-in">
          <div class="form wrap" v-if="currentStep === 2">
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
        </transition>
      </template>
    </WaitlistWrap>
    <transition appear mode="out-in">
      <div class="success-wrap" v-if="currentStep > 2">
        <waitlistSuccess />
      </div>
    </transition>
  </WaitlistLayout>
</template>

<script setup>
import { ref } from "vue";
import WaitlistLayout from "~/layouts/WaitlistLayout.vue";

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
    snippet:
      "Buy your food items with discounts, lesser prices and get them in 24hours",
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
  transition: all 1s;
}

.card {
  max-width: 507px;
}

.form {
  flex-direction: column;
  max-width: 354px;
}

.success-wrap {
  width: 100%;
  display: flex;
  justify-content: center;
}
/* Add the following styles for slide and fade effect */
.slidefade-enter-active,
.slidefade-leave-active {
  transition: all ease 0.4s;
}

.slidefade-enter,
.slidefade-leave-to {
  opacity: 0;
  transform: translateX(30px); /* Adjust the distance as needed */
}

.slidefade-enter {
  opacity: 0;
  transform: translateX(-30px); /* Negative value for entering from the left */
}
.slidefade-leave-to {
  transform: translateX(30px); /* Positive value for leaving to the right */
}

.v-enter-from {
  opacity: 0;
  translate: -100px 0px;
}

.v-enter-active {
opacity: 0.3;
translate: -50px -100px;
}

.v-enter-to {
  opacity: 1;
  translate: 0 0;
}
.v-leave-from {
  opacity: 1;
  translate: 0 0;
}
.v-leave-to {
  opacity: 0;
  translate: 100px 0;
}
</style>
