
<template lang="pug">
  div
    .container
      <Dz2_2/>

</template>

<script>
  import Dz2 from "./components/dz2.vue";
  import Dz2_2 from "./components/Dz2_2.vue";
  import styles from "./components/styles.vue";
  import styles2 from "./components/styles2.vue";

  export default {
    data() {
      return {

      }
    },
    components: {
      Dz2: Dz2,
      Dz2_2: Dz2_2,
      Styles: styles,
      Styles2: styles2
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

