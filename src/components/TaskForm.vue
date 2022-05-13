<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Form to create new task">
        <input
          type="text"
          class="input"
          placeholder="What task do you want to start?"
          v-model="description"
        />
      </div>

      <div class="column">
        <TaskTimer @onStopTimer="finishTask"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TaskTimer from "./TaskTimer.vue";

export default defineComponent({
  name: "TaskForm",
  emits: [
    'onTaskSave'
  ],
  data () {
    return {
      description: ''
    }
  },
  components: {
    TaskTimer,
  },
  methods: {
    finishTask(timeInSeconds: number): void {
      this.$emit('onTaskSave', {
        timeInSeconds,
        description: this.description
      })
      this.description = '';
    }
  }
});
</script>