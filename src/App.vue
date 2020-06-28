
<template lang="pug">
  div
    .container
      <AppDz2/>
</template>

<script>
  import Dz2 from "./components/dz2.vue";

  export default {
    data() {
      return {

      }
    },
    components: {
      AppDz2: Dz2
    }

  }
</script>

<style>
  .container {
    max-width: 600px;
    margin: auto;
  }

  input {
    width: 100%;
    max-width: 400px;
  }
</style>

