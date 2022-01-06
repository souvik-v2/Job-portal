<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>Job Portal</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by Tittle</button>
        <button @click="handleClick('location')">Order by Location</button>
        <button @click="handleClick('salary')">Order by Salary</button>
      </div>
    </header>
    <JobsList :jobs="jobs" :order="order" />
    <footer>
      <p>
        &copy; {{ period }} Design & Develop
        <a href="https://github.com/souvik-v2/Job-portal" target="_blank"
          >@souvik-v2</a> | (Vue3 + TypeScript)
      </p>
    </footer>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Job from "./types/job";
import OrderTerm from "./types/OrderTerm";
import JobsList from "./components/JobsList.vue";

export default defineComponent({
  name: "App",
  components: {
    JobsList,
  },
  setup() {
    const period = ref(new Date().getFullYear());
    const jobs = ref<Job[]>([
      {
        id: 1,
        title: "Software Engineer",
        location: "Bangalore",
        salary: 65000,
      },
      { id: 2, title: "Tester", location: "Mumbai", salary: 45000 },
      { id: 3, title: "HR", location: "Delhi", salary: 53000 },
      { id: 4, title: "Team Lead", location: "Chennai", salary: 82500 },
      { id: 5, title: "Farmer", location: "Pune", salary: 30000 },
      { id: 6, title: "Singer", location: "WB", salary: 35000 },
    ]);
    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return {
      period,
      jobs,
      handleClick,
      order,
    };
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
header .title {
  display: flex;
  justify-content: center;
}
header img {
  width: 60px;
  margin-right: 20px;
}
header h1 {
  font-size: 3em;
}
footer {
  text-align: center;
  font-size: 14px;
  font-weight: 700;
}
footer a {
  color: #1195c9;
  cursor: pointer;
}
</style>
