<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <FormatedTime :timeInSeconds="timeInSeconds" />

    <button class="button" @click="startTimer" :disabled="activeTimer">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>

    <button class="button" @click="stopTimer" :disabled="!activeTimer">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import FormatedTime from "./FormatedTime.vue";

export default defineComponent({
  name: "TaskTimer",
  emits: [
      `onStopTimer`
  ],
  components: {
    FormatedTime,
  },
  data() {
    return {
      timeInSeconds: 0,
      timerInterval: 0,
      activeTimer: false,
    };
  },
  methods: {
    startTimer() {
      this.activeTimer = true;
      this.timerInterval = setInterval(() => {
        this.timeInSeconds += 1;
      }, 1000);
    },
    stopTimer() {
      this.activeTimer = false;
      clearInterval(this.timerInterval);
      this.$emit('onStopTimer', this.timeInSeconds);
      this.timeInSeconds = 0;
    },
  },
});
</script>