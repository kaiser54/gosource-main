<template>
  <svg
    :class="{ selected: clicked, onHover: isHovered }"
    viewBox="0 0 25 25"
    width="20"
    height="20"
  >
    <circle cx="12" cy="12" r="11" />
    <path
      d="M8.5,12l2.5,2.5L15.5,10"
      fill="none"
      stroke="#fff"
      stroke-width="2"
      stroke-linecap="round"
      stroke-linejoin="round"
    />
  </svg>
</template>

<script setup>
defineProps({
  clicked: {
    type: Boolean,
    default: false,
  },
  isHovered: {
    type: Boolean,
    default: false,
  },
});
</script>

<style scoped>
svg {
  transition: opacity var(--animation-duration), transform var(--animation-duration);
}

svg circle {
  stroke: #e4e7ec;
  stroke-width: 1.66667px;
  fill: none;

  width: 100px;
  height: 100px;
  border-radius: 50%;
  opacity: 0.5;
  transition: all var(--animation-duration) ease-out;
}

svg path {
  width: 100px;
  height: 100px;
  transition: opacity var(--animation-duration), transform var(--animation-duration);
  opacity: 1;
}

.selected path {
  stroke-dasharray: 500;
  stroke-dashoffset: 500;
  animation: check 4s forwards;
}

svg.onHover circle {
  border: 1px solid var(--grey-300);
  stroke: var(--grey-300);
  opacity: 1;
}

.selected svg path {
  opacity: 1;
}
.selected {
  opacity: 1;
  animation: scaleAnimation var(--animation-duration) forwards;
}
.selected svg circle {
  stroke-width: 0;
  fill: #09420c;
  animation: scaleAnimation var(--animation-duration) forwards;
}
</style>
