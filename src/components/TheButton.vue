<template>
  <button class="button" @click="onClick" :disabled="disabled">
    <span class="icon">
      <i :class="icon"></i>
    </span>
    <span>{{ title }}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";

export default defineComponent({
  name: "TheButton",
  props: {
    title: {
      type: String,
      default: "",
    },
    icon: {
      type: String,
      default: "",
    },
    onClick: {
      type: Function,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
});
</script>

<style scoped>
button {
  color: var(--text-primary);
  background: var(--bg-primary);
}

button:disabled {
  color: var(--text-primary);
  background: var(--bg-primary);
}

button:hover,
button:active,
button:focus {
  color: var(--bg-primary);
  background: var(--text-primary);
  outline: none;
}
</style>