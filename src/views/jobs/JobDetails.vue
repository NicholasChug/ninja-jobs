<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <h2>{{ job.details }}</h2>
    <p>The job id is {{ id }}</p>
  </div>
  <div v-else>
    <p>Loading details...</p>
  </div>
</template>

<script>
export default {
    props: [
        'id'
    ],
    data() {
      return {
        job: null
      }
    },
    mounted() {
      fetch('http://localhost:3000/jobs/' + this.id)
        .then((res) => res.json())
        .then((data) => this.jobs = data)
        .catch((err) => console.log(err.message))
    }
}
</script>

<style>

</style>