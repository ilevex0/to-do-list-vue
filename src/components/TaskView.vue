<template>
  <div class="TaskView">
    <ul>
      <draggable v-model="taskList" :group="'taskList'" class="no-select">
        <li v-for="(task, index) in taskList" :key="index">
          <b-checkbox
            v-model="task.status"
            :class="task.status == false ? '' : 'task_finished'"
          >
            <span>{{ task.name }}</span>
            <b-button
              @click="removeModalShow(task, index)"
              class="button_delete"
              variant="danger"
              ><img src="../assets/lixeira.svg" alt="delete"
            /></b-button>
          </b-checkbox>
        </li>
      </draggable>
    </ul>
    <div class="add_task_button">
      <b-button @click="showModal" variant="primary">Add Task</b-button>
      <TaskModal ref="taskModal" @save="addTask" />
    </div>
  </div>
</template>

<script>
import TaskModal from "./TaskModal.vue";

import draggable from "vuedraggable";

export default {
  name: "TaskView",
  components: {
    TaskModal,
    draggable,
  },
  data() {
    return {
      taskList: [
        { name: "Tarefa 1", status: false },
        { name: "Tarefa 2", status: false },
      ],
    };
  },
  methods: {
    showModal() {
      this.$refs.taskModal.show();
    },
    hideModal() {
      this.$refs.taskModal.hide();
    },
    addTask(newTask) {
      this.taskList.push({
        name: newTask.name,
        status: newTask.status,
      });
    },
    removeModalShow(task, index) {
      this.$swal.fire({
        title: `Do you want to delete the task: ${task.name}?`,
        showDenyButton: true,
        showCancelButton: true,
        showConfirmButton: false,
        denyButtonText: `Delete`,
      }).then((result) => {
        /* Read more about isConfirmed, isDenied below */
        if (result.isDenied) {
          this.deleteTask(index);

          this.$swal.fire({
            position: "center",
            icon: "success",
            title: "Your task has been deleted.",
            showConfirmButton: false,
            timer: 1500,
          });
        }
      });
    },
    deleteTask(index) {
      this.taskList.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.no-select {
  user-select: none;
  cursor: grab;
}
ul {
  list-style-type: none;
}
li {
  padding: 5px;
  border-radius: 8px;
  margin: 10px;
  background-color: var(--site_color_two);
}
.task_finished span {
  text-decoration: line-through;
}
.button_delete {
  margin: 10px;
}
ol,
ul {
  padding-left: 0rem !important;
}
.add_task_button {
  margin: 20px;
}
</style>
