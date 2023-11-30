<template>
  <div class="step">
    <div class="ring onstep" :class="{ compleated: currentStep > 1 }">
      1
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="12"
        height="12"
        viewBox="0 0 12 12"
        fill="none"
      >
        <path
          d="M10 3L4.5 8.5L2 6"
          stroke="#F9FAFB"
          stroke-width="1.66667"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
      </svg>
    </div>
    <div class="bar">
      <span class="progress"></span>
    </div>
    <div class="ring" :class="{ compleated: currentStep === 3 }">
      2
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="12"
        height="12"
        viewBox="0 0 12 12"
        fill="none"
      >
        <path
          d="M10 3L4.5 8.5L2 6"
          stroke="#F9FAFB"
          stroke-width="1.66667"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
      </svg>
    </div>
  </div>
</template>

<script setup>
defineProps({
  currentStep: {
    type: Number,
    required: true,
  },
});
</script>

<style scoped>
.step {
  display: flex;
  align-items: center;
  gap: 8px;
}
.ring {
  display: flex;
  width: 24px;
  height: 24px;
  padding: 10px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 10px;

  color: var(--grey-300, #d0d5dd);
  font-family: Inter;
  font-size: 12px;
  font-style: normal;
  font-weight: 600;
  line-height: 18px; /* 150% */

  border-radius: 24px;
  border: 1px solid var(--grey-300, #d0d5dd);
}

.ring svg {
  position: absolute;
  opacity: 0;
  transition: opacity var(--animation-duration), transform var(--animation-duration);
}

.onstep,
.compleated ~ .ring {
  color: var(--success-500-base, #099137);
  border: 1px solid var(--success-500-base, #099137);
  animation: all var(--animation-duration) ease-in-out;
}

.bar {
  position: relative;
  width: 90px;
  height: 2px;
  border-radius: 2px;
  background: var(--success-50, #e7f6ec);
}

.progress {
  position: absolute;
  width: 50%;
  height: 100%;
  border-radius: 2px;
  background: var(--success-500-base, #099137);
}

.onstep,
.bar,
.progress {
  animation: scaleAnimation 0.3s forwards;
}

.compleated {
  background: var(--success-500-base);
}

.compleated ~ .bar .progress {
  width: 100%;
}


.compleated svg {
  opacity: 1;
}

.compleated svg path {
  stroke-dasharray: 500;
  stroke-dashoffset: 500;
  animation: check 4s forwards;
}
</style>
