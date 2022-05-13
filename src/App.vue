<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <TaskForm @onTaskSave="saveTaskItem" />
      <div class="list">
        <TaskItem
          v-for="(task, index) in taskItems"
          :key="index"
          :taskItem="task"
        />
        <BoldBox v-if="!hasTaskItems">
          No task registered yet :(
        </BoldBox>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBar from "@/components/SideBar.vue";
import TaskForm from "@/components/TaskForm.vue";
import TaskItem from "@/components/TaskItem.vue";
import BoldBox from '@/components/BoldBox.vue';
import ITaskItem from "@/interfaces/ITaskItem";

export default defineComponent({
  name: "App",
  components: {
    SideBar,
    TaskForm,
    TaskItem,
    BoldBox
  },
  data() {
    return {
      taskItems: [] as ITaskItem[],
    };
  },
  computed: {
    hasTaskItems(): boolean {
      return this.taskItems.length > 0
    }
  },
  methods: {
    saveTaskItem(taskItem: ITaskItem): void {
      this.taskItems.push(taskItem);
    },
  },
});
</script>

<style>
.list {
  padding: 1.25rem;
}
</style>
