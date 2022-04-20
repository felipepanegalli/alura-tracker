<template>
  <header>
    <h1>
      <img src="@/assets/logo.png" alt="Header" />
    </h1>
    <Toggle
      id="darMode"
      v-model="value"
      @change="changeTheme"
      on-label="Light"
      off-label="Dark"
    />
  </header>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import Toggle from "@vueform/toggle";
import "@vueform/toggle/themes/default.css";

export default defineComponent({
  name: "TheSidebar",
  emits: ["onChangeTheme"],
  components: {
    Toggle,
  },
  data() {
    return {
      darkMode: false,
      value: false,
    };
  },
  computed: {
    textDarkMode: function (): string {
      return this.darkMode ? "Light Mode" : "Dark Mode";
    },
  },
  methods: {
    changeTheme: function (): void {
      this.darkMode = !this.darkMode;
      this.$emit("onChangeTheme", this.darkMode);
    },
  },
});
</script>

<style scoped>
header {
  padding: 1rem;
  width: 100%;
  height: 100vh;
  background: var(--bg-info);
  text-align: center;
}

::v-deep .toggle {
  width: var(--toggle-width, 3.5rem);
  outline: none;
}

::v-deep .toggle-label{
  margin: auto 3px;
}

button {
  cursor: pointer;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>