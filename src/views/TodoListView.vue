<template>
  <div class="flex justify-center gap-4 items-center flex-col py-10">
    <h1 class="text-xl text-teal-500 font-bold">Add Tasks and remove it</h1>
    <form @submit.prevent="addTasktoList" class="flex gap-4">
      <input
        class="border border-gray-400 p-2 rounded-lg"
        v-model="tasktext"
        placeholder="add task"
      />
      <button
        class="bg-blue-500 p-4 text-center font-bold text-white rounded-lg"
        type="submit"
      >
        Submit
      </button>
    </form>
    <div class="w-full" v-if="tasksList.length > 0">
      <ul>
        <li
          class="my-1 p-1 border border-gray-100 font-medium rounded-sm w-full"
          v-for="(task, index) in tasksList"
          :key="index"
          @click="removeTask(index)"
        >
          {{ task }}
        </li>
      </ul>
    </div>
    <div v-else>No tasks added yet.</div>
  </div>
</template>

<script>
export default {
  name: "todo",
  data() {
    return {
      tasktext: "",
      tasksList: [],
    };
  },
  methods: {
    addTasktoList() {
      this.tasksList.push(this.tasktext);
      this.tasktext = ""; // Clear input after adding the task
    },
    removeTask(index) {
      this.tasksList.splice(index, 1);
    },
    logValues() {
      console.log("This is tasklist", this.tasksList);
    },
  },
};
</script>
