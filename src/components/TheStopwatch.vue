<template>
  <section>
    <strong class="display">{{ currentTimer }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";

export default defineComponent({
  name: "TheStopwatch",
  props: {
    timerInSeconds: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    currentTimer: function (): string {
      return new Date(this.timerInSeconds * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>

<style scoped>
.display {
  color: var(--text-primary);
}
</style>