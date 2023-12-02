<template>
  <div class="wrap-wrapper">
    <div class="progress-header">
      <WaitlistProgressBar :currentStep="currentStep" />
      <div
        class="header-content"
        :class="{ step1: currentStep === 1, step2: currentStep === 2 }"
      >
        <h3 class="medium text-heading-3-medium">{{ data[currentStep - 1]?.title }}</h3>
        <p class="regular text-body-large-regular text-grey-500">
          {{ data[currentStep - 1]?.snippet }}
        </p>
      </div>
    </div>
    <slot name="content"></slot>
    <DynamicButtonMain
      class="bold text-button-large w-auto"
      size="large"
      type="primary"
      :buttonText="data[currentStep - 1]?.buttonText || 'continue'"
      :isLoading="false"
      :disabled="disabled"
      @clickButton="$emit('clickButton')"
    />
  </div>
</template>

<script setup>
defineProps({
  data: {
    type: Object,
    required: true,
  },
  currentStep: {
    type: Number,
    required: true,
  },
  disabled: {
    type: Boolean,
    required: false,
  },
});
</script>

<style scoped>
.wrap-wrapper {
  margin-left: 21%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: calc(var(--spacing-unit) * 6);
  padding-bottom: 60px;
}

.progress-header {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: calc(var(--spacing-unit) * 3);
}

.header-content {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: var(--spacing-unit);
}

.step1 {
  max-width: 396px;
}
.step2 {
  max-width: 354px;
}

@media (max-width: 750px) {
  .wrap-wrapper {
    max-width: fit-content;
    margin-inline: auto;
  }
}

@media (max-width: 450px) {
  .progress-header {
    align-items: center;
  }
  h3 {
    font-size: var(--h3---heading-3--small--medium);
    font-style: normal;
    font-weight: 500;
    line-height: 30px; /* 150% */
    letter-spacing: -0.3px;
  }
  p {
    font-size: var(--body--small---body--small--bold);
  }
}
</style>
