<template>
  <label>{{ label }}</label>
  <input
    v-bind="$attrs"
    class="field"
    :placeholder="label"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  >
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      default: ''
    },
    // default v-model prop from vue 3
    modelValue: {
      type: [String, Number],
      default: ''
    }
  }
}
</script>
