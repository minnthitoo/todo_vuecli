<template>
  <div id="app">
    <h1 class="text-center bg-primary text-white p-3">
      <font-awesome-icon icon="fa-solid fa-user-secret" />{{ title }}'s' Todo
      List
    </h1>
    <div class="container">
      <div class="row bg-danger">
        
        <div class="col fs-3">Tasks<font-awesome-icon icon="fa-solid fa-house" /></div>
        <div class="col-2 fs-3">Done</div>
      </div>
      <div class="row mt-2" v-for="(task, index) in filterTask" :key="index">
        <div class="col" v-bind:class="task.done ? 'delete' : ''">
          {{ task.title }}
        </div>
        <div class="col-2">
          <input type="checkbox" v-model="task.done" />
        </div>
      </div>
      <div class="row mt-3">
        <div class="col bg-danger text-center text-white p-2">
          <h5>Hide completed tasks</h5>
          <input type="checkbox" v-model="completed"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    title: "CODE LAB",
    completed: false,
    tasks: [
      {
        title: "Buy new Phone",
        done: true,
      },
      {
        title: "Buy new Computer",
        done: true,
      },
      {
        title: "Buy new Car",
        done: false,
      },
      {
        title: "Buy new Aeroplane",
        done: false,
      },
      {
        title: "Buy new satellite",
        done: false,
      },
    ],
  }),
  computed: {
    filterTask(){
      return this.completed ? this.tasks.filter((v) => !v.done) : this.tasks;
    }
  },
};
</script>

<style>
.delete {
  text-decoration: line-through;
}
</style>
