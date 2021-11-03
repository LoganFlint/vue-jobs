<template>
  <div id="app" class="bg-speedOfLight min-h-screen px-40">
    <button
      class="border bg-blue border-unicornSilver"
      @click="handleClick('location')"
    >
      Order by location
    </button>
    <button
      class="border bg-darkPurple border-unicornSilver"
      @click="handleClick('salary')"
    >
      Order by salary
    </button>
    <button
      class="border border-unicornSilver bg-darkOrange"
      @click="handleClick('title')"
    >
      Order by title
    </button>
    <JobList :jobs="state.jobList" :order="clickedOrder" />
  </div>
</template>

<script lang="ts">
import JobList from "./components/JobList.vue";
import { Jobs, OrderTerms } from "./types/jobs";

import { defineComponent, reactive, ref } from "vue";

export default defineComponent({
  name: "App",
  components: {
    JobList,
  },
  setup() {
    const state = reactive({
      jobList: [
        {
          title: "Software Engineer",
          location: "Sacramento",
          salary: 70000,
          id: 17029374,
        },
        {
          title: "Network Engineer",
          location: "Los Angelas",
          salary: 100000,
          id: 17029263,
        },
        {
          title: "Back End Developer",
          location: "Reno",
          salary: 80000,
          id: 17029859,
        },
        {
          title: "Mobile Developer",
          location: "Boston",
          salary: 110000,
          id: 17029236,
        },
        {
          title: "Intern Dev",
          location: "Portland",
          salary: 30000,
          id: 17029162,
        },
      ] as Jobs[],
    });

    const clickedOrder = ref<OrderTerms>("title");

    function handleClick(order: OrderTerms) {
      clickedOrder.value = order;
    }
    return { state, clickedOrder, handleClick };
  },
});
</script>
