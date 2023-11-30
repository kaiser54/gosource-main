<template>
  <button class="account-wrapper bg-orange-50">
    <div class="group">
      <div class="avartar bg-orange-500">{{ initial }}</div>
      <div class="avartar-name text-grey-900-base text-heading-5-medium">
        {{ name || "temitope a." }}
      </div>
    </div>
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="12"
      height="12"
      viewBox="0 0 12 12"
      fill="none"
    >
      <path
        d="M9.96004 4.4751L6.70004 7.7351C6.31504 8.1201 5.68504 8.1201 5.30004 7.7351L2.04004 4.4751"
        stroke="#667185"
        stroke-width="1.5"
        stroke-miterlimit="10"
        stroke-linecap="round"
        stroke-linejoin="round"
      />
    </svg>
  </button>
  <div class="menu bg-grey-100"></div>
</template>

<script setup>
import { ref, computed } from "vue";
const { name } = defineProps({
  name: {
    type: String,
    required: true,
  },
});

const initial = computed(() => {
  return name.charAt(0).toUpperCase();
});
</script>

<style scoped>
button.account-wrapper {
  display: inline-flex;
  padding: var(--spacing-unit) calc(var(--spacing-unit) * 2) var(--spacing-unit)
    var(--spacing-unit);
  align-items: center;
  gap: calc(var(--spacing-unit) * 3);

  border-radius: 100px;
  width: auto;
}
button .group {
  display: flex;
  gap: var(--spacing-unit);
  align-items: center;
}
.avartar {
  display: flex;
  width: calc(var(--spacing-unit) * 4);
  height: calc(var(--spacing-unit) * 4);
  padding: calc(var(--spacing-unit) - 3);
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: calc(var(--spacing-unit) + 2);
  border-radius: calc(var(--spacing-unit) * 10);
  color: var(--white);
  font-size: var(--h5---heading-5--bold);
  font-weight: 600;
  line-height: 27px; /* 150% */
  letter-spacing: -0.2px;
}
.avartar-name {
  overflow: hidden;
  text-overflow: ellipsis;
  letter-spacing: -0.2px;
}
.menu {
  display: flex;
  padding: var(--spacing-unit) 0px;
  flex-direction: column;
  align-items: flex-start;
  gap: calc(var(--spacing-unit) / 2);

  border-radius: calc(var(--spacing-unit) + 4);
  border: 1px solid var(--grey-100);
  background: var(--white);
  box-shadow: var(--shadow---shadow__-medium);
}
</style>
