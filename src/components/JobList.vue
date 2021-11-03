<template>
  <div>
    <div>ordered by {{ order }}</div>
    <ul>
      <li
        v-for="(job, i) in orderedJobs"
        :key="i"
        :class="[
          'pl-5 pr-20',
          { 'bg-lightOrange': i % 2 === 0 },
          { 'bg-lightPurple': i % 2 !== 0 },
        ]"
      >
        <div>{{ job.title }} in {{ job.location }}</div>
        <div>
          <div>{{ job.salary }} USD / salary</div>
        </div>
        <div>
          <div>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Odio eum
            reprehenderit voluptatum quo omnis atque sunt, ab repellat expedita
            accusantium minus dolor voluptate ullam deleniti blanditiis porro
            ipsam similique voluptatibus.
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Jobs, OrderTerms } from "@/types/jobs";
import { computed, defineComponent, PropType, reactive } from "vue";

export default defineComponent({
  props: {
    jobs: {
      type: Array as PropType<Jobs[]>,
      required: true,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerms>,
    },
  },
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Jobs, b: Jobs) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });
    return { orderedJobs };
  },
});
</script>
