
<template lang="pug">
  .container
    h2 {{numberTitle2}}
    button.btn.btn-primaty(@click="onClick") +
    hr

</template>

<script>

export default {
  name: "appSome",
  props: ['numberTitle'],
  data() {
    return {

    }
  },
  methods: {
    onClick(e) {
      this.$emit('plusplus')
    },
    numberTitle2(i) {
      this.$emit('numbernumber')
    }
  }
}

</script>

<style scoped>

</style>
