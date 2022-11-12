<template>
  <div>
    <h1 class="text-center bg-primary text-white p-3">
      {{ title }}'s Todo
      List
    </h1>
    <div class="container">
      <div class="row mt-3">
        <div class="input-group mb-3">
          <input
            type="text"
            class="form-control"
            v-model="newTask"
            v-on:keyup.enter="add()"
            placeholder="New Tesk"
            aria-label="New Tesk"
            aria-describedby="button-addon2"
          />
          <button
            class="btn btn-outline-secondary"
            type="button"
            id="button-addon2"
            @click="add()"
          >
            Add
          </button>
        </div>
      </div>
      <div class="" v-if="filterTask.length > 0">
        <div class="row">
          <div class="col fs-3">
            Tasks
          </div>
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
            <input type="checkbox" v-model="completed" />
          </div>
        </div>
      </div>
      <div class="" v-else>
        <div class="alert alert-warning">There is no Data</div>
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
    newTask: "",
    tasks: [],
  }),
  computed: {
    filterTask() {
      return this.completed ? this.tasks.filter((v) => !v.done) : this.tasks;
    },
  },
  methods: {
    add() {
      if (this.newTask == "") {
        return alert("Enter some word");
      }
      this.tasks.push({
        title: this.newTask,
        done: false,
      });
      this.newTask = "";
    },
  },
};
</script>

<style>
.delete {
  text-decoration: line-through;
}
</style>
