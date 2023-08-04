<template>
  <div v-if="jobData">
    <h1>Job Details Page</h1>
    <h2>{{ jobData.title }}</h2>
    <p>{{ jobData.details }}</p>
  </div>
  <div v-else>
    <p>Loading job details...</p>
  </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      jobData: null,
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.jobData = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style></style>
