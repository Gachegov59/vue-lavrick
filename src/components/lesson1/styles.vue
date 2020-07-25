<template lang="pug">
  .container
    section
      .alert.alert-info(:class="divClassName") {{divClass}}
      .form-check.d-flex
        label.form-check-label info
        input.form-check-input(type="radio" value="info" v-model="divClass")
      .form-check.d-flex
        label.form-check-label warning
        input.form-check-input(type="radio" value="warning" v-model="divClass")
      hr


    section
      .form-check.d-flex(v-for="(value, name) in flags")
        label.form-check-label {{name}}
        input.form-check-input(type="checkbox" v-model="flags[name]" )

      table.table(:class="flags")
        tbody
          tr
            td Title
            td Some
            td nZ
          tr
              td Title
              td Some
              td nZ
          tr
              td Title
              td Some
              td nZ

</template>

<script>
  export default {
    name: "styles",
    data() {
      return {
        divClass: 'warning',
        flags: {
            'table-bordered': true,
            'table-hover': true,
            'table-some': false,
        }
      }
    },
    computed: {
      divClassName() {
        return [
          'alert-' + this.divClass,
          'my-' + this.divClass
        ]
      }
    }
  }

</script>

<style>
  .my-info {
    color: dodgerblue;
  }
  .my-waring {
    color: brown;
  }

</style>
