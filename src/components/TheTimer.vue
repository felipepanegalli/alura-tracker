<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between is-1">
    <TheStopwatch :timerInSeconds="timerInSeconds" />
    <TheButton
      title="Play"
      icon="fas fa-play"
      :onClick="startTimer"
      :disabled="stopwatchIsRunning"
    />
    <TheButton
      title="Stop"
      icon="fas fa-stop"
      :onClick="stopTimer"
      :disabled="!stopwatchIsRunning"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import TheStopwatch from "@/components/TheStopwatch.vue";
import TheButton from "./TheButton.vue";

export default defineComponent({
  name: "TheTimer",
  components: { TheStopwatch, TheButton },
  emits: ["onTimerStop"],
  data() {
    return {
      timerInSeconds: 0,
      stopwatch: 0,
      stopwatchIsRunning: false,
    };
  },
  methods: {
    startTimer: function () {
      this.stopwatchIsRunning = true;
      this.stopwatch = setInterval(() => {
        this.timerInSeconds += 1;
      }, 1000);
    },
    stopTimer: function () {
      this.stopwatchIsRunning = false;
      clearInterval(this.stopwatch);
      this.$emit("onTimerStop", this.timerInSeconds);
      this.timerInSeconds = 0;
    },
  },
});
</script>

<style scoped>
</style>