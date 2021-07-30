<template>
  <button :type="type" class="btn" :class="['btn-' + variant]">
    <slot />
  </button>
</template>


<script lang="ts">
import Vue from "vue";

const TYPES = ["button", "submit", "reset"];

const VARIANTS = ["primary", "second", "third", "info", "danger", "warning"];

export default /*#__PURE__*/ Vue.extend({
  name: "lButton", // vue component name
  props: {
    variant: {
      type: String,
      default: "primary",
      required: false,
      validator(value) {
        const isValid = VARIANTS.includes(value);
        if (!isValid) {
          console.warn(`allowed variants are ${VARIANTS}`);
        }
        return isValid;
      },
    },
    type: {
      type: String,
      required: false,
      default: "button",
      validator(value) {
        const isValid = TYPES.includes(value);
        if (!isValid) {
          console.warn(`allowed types are ${TYPES}`);
        }
        return isValid;
      },
    },
  },
});
</script>

<style>
</style>
