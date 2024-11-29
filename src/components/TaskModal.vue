<template>
  <b-modal id="modal-1" title="Add Task" @ok="save">
    <div role="group">
      <label for="input-live">Task name:</label>
      <b-form-input
        id="input-live"
        v-model="newTask.name"
        :state="nameState"
        aria-describedby="input-live-help input-live-feedback"
        placeholder="Enter your task"
        trim
      ></b-form-input>

      <!-- This will only be shown if the preceding input has an invalid state -->
      <b-form-invalid-feedback id="input-live-feedback">
        Enter at least 6 letters
      </b-form-invalid-feedback>

      <!-- This is a form text block (formerly known as help block) -->
      <b-form-text id="input-live-help">The name of the Task.</b-form-text>
    </div>
  </b-modal>
</template>

<script>

export default {
  name: "TaskModal",
  computed: {
    nameState() {
      return this.newTask.name.length > 5 ? true : false;
    },
  },
  methods: {
    show() {
      this.$bvModal.show("modal-1");
    },
    hide() {
      this.$bvModal.hide("modal-1");
    },
    save() {
      if (this.newTask.name.length > 5) {
        this.$emit("save", this.newTask);
      } else {
        this.$swal.fire({
          icon: "error",
          title: "Oops...",
          text: "The Task Name needs to be at least 6 letters.",
        });
      }
    },
  },
  data() {
    return {
      newTask: { name: "", status: false },
    };
  },
};
</script>

<style scoped></style>
