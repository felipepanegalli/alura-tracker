<template>
  <div class="box has-text-weight-bold">
      <slot></slot>  
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "TheBox",
});
</script>

<style scoped>
.box {
  background: #fbc531;
  margin: 0.75rem 0;
}
</style>