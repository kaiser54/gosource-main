<template>
  <div class="wrapper">
    <img src="/images/success.svg" alt="" />
    <div class="content">
      <h3 class="text-heading-3-medium medium text-grey-900-base">
        You’ve been successfully added to the waitlist!
      </h3>
      <p class="text-body-large-regular regular text-grey-500">
        We will let you know when you’ve been given access to join the Private
        Beta testing.
      </p>
    </div>
    <DynamicButtonMain
      class="bold text-button-large w-auto"
      size="large"
      type="primary"
      buttonText="Go to website"
      :isLoading="false"
      @clickButton="$emit('clickButton')"
    />
  </div>
</template>

<script setup>
</script>

<style scoped>
.wrapper {
  display: flex;
  max-width: 329px;
  width: 100%;
  flex-direction: column;
  align-items: center;
  gap: 39px;
}
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--spacing-unit);
  align-self: stretch;
  text-align: center;
}
</style>