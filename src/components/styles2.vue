<template lang="pug">
  .container
    section
      .alert.alert-info(:style="properties") keke


      table.table.table-bordered
        tbody
          tr(v-for="(value, name) in properties")
            td {{name}}
            td
              input(type="text" v-model="properties[name]")
          tr


</template>

<script>
  export default {
    name: "styles2",
    data() {
      return {
        properties: {
          color: 'inherit',
          backgroundColor: 'none'
        }
      }
    },
  }

</script>

<style>


</style>
