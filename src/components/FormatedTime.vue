<template>
  <section>
    <strong>{{ formatedTime }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "FormatedTime",
  props: {
    timeInSeconds: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    formatedTime(): string {
      return new Date(this.timeInSeconds * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>