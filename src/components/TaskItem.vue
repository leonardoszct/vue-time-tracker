<template>
  <BoldBox>
    <div class="columns">
      <div class="column is-7">
        {{ taskItem.description || "Tarefa sem descrição" }}
      </div>
      <div class="column">
        <FormatedTime :timeInSeconds="taskItem.timeInSeconds" />
      </div>
    </div>
  </BoldBox>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import FormatedTime from "./FormatedTime.vue";
import BoldBox from './BoldBox.vue';
import ITaskItem from "@/interfaces/ITaskItem";

export default defineComponent({
  name: "TaskItem",
  components: {
    FormatedTime,
    BoldBox
  },
  props: {
    taskItem: {
      type: Object as PropType<ITaskItem>,
      required: true,
    },
  },
});
</script>

<style scoped>
</style>