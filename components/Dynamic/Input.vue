<template>
  <div class="input-box">
    <label :class="{ focus: isFocused || modelValue.length > 0 }">{{ labelText }}</label>
    <input
      class="input"
      type="text"
      :class="{ error: isError }"
      :value="modelValue"
      :disabled="disabled"
      @input="$emit('update:modelValue', $event.target.value)"
      @focus="handleFocus()"
      @blur="handleBlur()"
    />
  </div>
</template>

<script setup>
defineProps({
  labelText: {
    type: String,
    default: false,
  },
  modelValue: {
    type: String,
    default: "",
  },
  isError: {
    type: Boolean,
    default: false,
  },
  disabled: {
    type: Boolean,
    default: false,
  },
});

const isFocused = ref(false);

const handleFocus = () => {
  isFocused.value = true;
};
const handleBlur = () => {
  isFocused.value = false;
};
</script>
