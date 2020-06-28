<template lang="pug">
  div
    <h2>Circles: {{ circles }}</h2>
    <p>Runner's status: {{ getRunnerStatus() }}</p>
</template>

<script>
  export default {
    name: "circle",
    data() {
      return {
        circles: 0,
        finished: false
      }
    },
    methods: {
      getRunnerStatus() {
        console.log('hi')

        return this.finished ? 'finished' : 'running'
      }
    },

    created() {
      setInterval(() => this.circles++, 1000)
    }

  }
</script>

<style scoped>

</style>
