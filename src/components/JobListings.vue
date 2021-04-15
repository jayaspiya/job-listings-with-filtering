<template>
  <ul>
    <job-list
      v-for="job in filteredJoblist"
      :job="job"
      :key="job.id"
    ></job-list>
  </ul>
</template>

<script>
import JobList from "./JobList.vue";
export default {
  components: {
    JobList,
  },
  data() {
    return {
      filteredJoblist: [...this.joblist],
    };
  },
  inject: ["joblist", "filterOption"],
};
</script>
