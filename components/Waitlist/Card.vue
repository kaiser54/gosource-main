<template>
  <div
    class="flex border select-card"
    :class="{ selected: selectedItem === data.value }"
    @mouseover="handleMouseOver"
    @mouseleave="handleMouseLeave"
    @click="$emit('selectEvent', data.value)"
  >
    <div class="img-select flex">
      <img :src="data.img" alt="" />
      <div class="radio">
        <CheckBox :isHovered="isHovered" />
      </div>
    </div>
    <div class="content">
      <h4 class="bold text-heading-4-bold text-grey-700">{{ data.title }}</h4>
      <p class="regular text-body-small-regular text-grey-500">{{ data.snippet }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
const { data, selectedItem } = defineProps({
  data: {
    type: Object,
    required: true,
  },
  selectedItem: {
    type: String,
    required: true,
  },
});

const isHovered = ref(false);
const handleMouseOver = () => {
  isHovered.value = true;
};

const handleMouseLeave = () => {
  isHovered.value = false;
};

</script>

<style>
.flex {
  display: flex;
}
</style>

<style scoped>
.select-card {
  padding: 20px;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  gap: calc(var(--spacing-unit) * 3);
  cursor: pointer;
  max-width: 237.5px;
  width: 100%;
  border-radius: calc(var(--spacing-unit) * 2);
  border: 1px solid var(--grey-100);
  background: var(--White);

  transition: all 0.3s ease-out;
}

.content {
  flex-direction: column;
  align-items: flex-start;
  gap: var(--spacing-unit);
}

.select-card:hover {
  border: 1px solid var(--grey-300);
  stroke: var(--grey-300);
  opacity: 1;
}

.img-select {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.selected {
  border: 1px solid var(--orange-orange-300);
  background: var(--orange-orange-25);
}

.selected:hover {
  border: 1px solid var(--orange-orange-300);
}

</style>