<template>
  <div class="box form">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para ciração de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="task"
        />
      </div>
      <div class="column">
        <TheTimer @onTimerStop="stopTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import TheTimer from "./TheTimer.vue";

export default defineComponent({
  components: { TheTimer },
  name: "TheFrom",
  emits: ["onSaveTask"],
  data() {
    return {
      task: "",
      tasks: [],
    };
  },
  methods: {
    stopTask: function (currentTimer: number): void {
      this.$emit("onSaveTask", {
        timerInSeconds: currentTimer,
        description: this.task,
      });
      this.task = "";
    },
  },
});
</script>

<style scoped>
.form {
  color: var(--text-primary);
  background: var(--bg-primary);
}
</style>