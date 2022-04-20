<template>
  <main
    class="columns is-gapless is-multiline"
    :class="{ 'dark-mode': darkMode }"
  >
    <div class="column is-one-quarter">
      <TheSidebar @onChangeTheme="changeTheme" />
    </div>
    <div class="column is-three-quarter content">
      <TheForm @onSaveTask="saveTask" />
      <div class="list">
        <TheTask v-for="(task, i) in tasks" :key="i" :task="task" />
        <TheBox v-if="listIsEmpty">
          Você não tem tarefas iniciadas hoje.
        </TheBox>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TheTask from "./components/TheTask.vue";
import TheForm from "./components/TheForm.vue";
import TheSidebar from "./components/TheSidebar.vue";
import ITheTask from "./interfaces/ITheTask";
import TheBox from "./components/TheBox.vue";

export default defineComponent({
  name: "App",
  components: { TheSidebar, TheForm, TheTask, TheBox },
  data() {
    return {
      tasks: [] as ITheTask[],
      darkMode: false,
    };
  },
  computed: {
    listIsEmpty: function (): boolean {
      return this.tasks.length === 0;
    },
  },
  methods: {
    saveTask: function (task: ITheTask) {
      this.tasks.push(task);
    },
    changeTheme: function (theme: boolean): void {
      this.darkMode = theme;
    },
  },
});
</script>

<style scoped>
.list {
  padding: 0 0.5rem;
}

main {
  --bg-primary: #f5f6fa;
  --bg-info: #487eb0;
  --text-primary: #353b48;
}

main.dark-mode {
  --bg-primary: #353b48;
  --bg-info: #00a8ff;
  --text-primary: #f5f6fa;
}

.content {
  background: var(--bg-primary);
}
</style>
