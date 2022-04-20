<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">{{ task.description || 'Tarefa sem descrição' }}</div>
      <div class="column">
        <TheStopwatch :timerInSeconds="task.timerInSeconds" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import ITheTask from "@/interfaces/ITheTask";
import { defineComponent, PropType } from "vue";
import TheStopwatch from "./TheStopwatch.vue";
export default defineComponent({
  components: { TheStopwatch },
  name: "TheTask",
  props: {
    task: {
      type: Object as PropType<ITheTask>,
      required: true,
    },
  },
});
</script>

<style scoped>
.box {
  background: #fbc531;
  margin: 0.75rem 0;
  color: #705201;
}
</style>