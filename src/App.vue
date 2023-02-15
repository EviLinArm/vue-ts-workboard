<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>Jobs Board</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order"/>
  </div>
</template>

<script lang="ts">
import {defineComponent, reactive, ref} from 'vue';
import Job from "./types/Job";
import JobList from "./components/JobList.vue";
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: 'App',
  components: {JobList},
  setup() {
    const jobs = ref<Job[]>([
      {
        title: 'farm worker',
        salary: 30000,
        location: 'lon lon ranch',
        id: '1'
      },
      {
        title: 'flute player',
        salary: 40000,
        location: 'death mountain',
        id: '2'
      },
      {
        title: 'fisherman',
        salary: 70000,
        location: 'lake hylia',
        id: '3'
      },
      {
        title: 'prison guard',
        salary: 99000,
        location: 'gerudo valley',
        id: '4'
      },
      {
        title: 'quarryman',
        salary: 3000,
        location: 'the lost woods',
        id: '5'
      },
    ])
    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return {jobs, handleClick, order}
  },
});
</script>

<style>
header {
  text-align: center;
}

header .order {
  margin-top: 20px;
}

button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>

