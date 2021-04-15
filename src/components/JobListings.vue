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
  computed: {
    filteredJoblist() {
      if (this.filterOption.length === 0) {
        return this.theJoblist;
      }
      return this.theJoblist.filter((job) => {
        const skills = [job.role, job.level, ...job.languages, ...job.tools];
        const intersection = this.filterOption.filter((element) =>
          skills.includes(element)
        );
        if (intersection.length === this.filterOption.length) {
          return true;
        }
        return false;
      });
    },
  },
  data() {
    return {
      theJoblist: [...this.joblist],
    };
  },
  inject: ["joblist", "filterOption"],
};
</script>
