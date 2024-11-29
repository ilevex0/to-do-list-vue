<template>
  <div id="app">
    <p class="project_title">Project / To do list</p>
    <hr>

    <section class="taskViewSection">
      <TaskView />
    </section>
    <hr>
  </div>
</template>

<script>
import TaskView from "./components/TaskView.vue";

export default {
  name: "App",
  components: {
    TaskView,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Kanit:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Mina:wght@400;700&family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');
/*
@import 'bootstrap/dist/css/bootstrap.css';
@import 'bootstrap-vue/dist/bootstrap-vue.css';
*/
:root {
/*
--site_color_one: rgb(146, 146, 146); background task
--site_color_two: lightGray;  Tasks 
--site_color_text: #1b2631;  text 
*/

--site_color_one: rgb(223, 223, 223); /* background task */
--site_color_two: rgba(255, 255, 255, 0.658); /* Tasks */
--site_color_text: #1b2631; /* text */
--site_color_body: rgb(98, 105, 117);
}
html {
  background-color: var(--site_color_body);
}
#app {
  font-family: "Mina", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--site_color_text);
  margin-top: 60px;
  background-color: var(--site_color_body);
}
.project_title {
  display: flex;
  margin: 0 0 10px 30px;
  font-weight: 600;
}
.taskViewSection {
  align-self: center;
  justify-self: center;
  max-width: 80%;
  align-content: center;
  justify-content: center;
  margin: auto;
  background-color: var(--site_color_one);
  border-radius: 8px;
}
.custom-control-label::after {
    top: 1.1rem;
    left: -1.5rem;
}
.custom-control-label::before {
    top: 1.1rem;
    left: -1.5rem;
}

</style>
