<template>
  <div v-for="job in jobs" :key="job.id" class="job">
    <router-link :to="{ name: 'jobDetails', params: {id: job.id} }">
      <h4>{{ job.title }}</h4>
    </router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      jobs: []
          // [
        // {id: 1, title: "Web Developer", details: ""},
        // {id: 2, title: "Web Designer", details: ""},
        // {id: 3, title: "PM", details: ""}
      // ]
    }
  },
  mounted() {
    fetch("http://localhost:3000/jobs")
        .then(res => res.json())
        .then(data => this.jobs = data)
        .catch(err => err.message);
  }
}
</script>

<style scoped>
  .job {
    background: #f4f4f4;
    padding: 10px;
    border-radius: 10px;
    margin: 10px auto;
    max-width: 400px;
    cursor: pointer;
    color: #444;
  }
  .job h2:hover {
    background: #ddd;
  }
  .job a {
    text-decoration: none;
  }
</style>
