<template>
  <h1>Job Details</h1>
  <div v-if="job">
    <div>Job's ID is {{ id }}</div>
    <div>Job's Title is {{ job.title }}</div>
    <div>Job's Details is {{ job.details }}</div>
  </div>
  <div v-else>Job Details loading...</div>
</template>

<script>
export default {
  props: ['id'],
  name: "JobDetails",
  data() {
    return {
      job: null
    }
  },
  mounted() {
    fetch(`http://localhost:3000/jobs/${this.$props.id}`)
        .then(res => res.json())
        .then(data => this.job = data)
        .catch(err => err.message)
  }
}
</script>

<style scoped>

</style>
