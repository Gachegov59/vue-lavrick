<template lang="pug">
  div
    .progress
      .progress-bar(role="progressbar" aria-valuenow="50" aria-valuemax="100" style="width: 0")

    form(@submit.prevent="formSubmited = true")

      .form-group.mb-1(v-for="(item, key, i) in info")
        label {{item.name}} <span class="fas fa-check-circle color-green"></span>
          input(v-model="checkInput"  )

      hr
      button.btn.btn-primary(disabled) Send Data
</template>

<script>
  export default {
    name: "dz2",

    data() {
      return {
        info: [
          {
            name: 'Name',
            value: '',
            pattern: /^[a-zA-Z ]{2,30}$/
          },
          {
            name: 'Phone',
            value: '',
            pattern: /^[0-9]{7,14}$/
          },
          {
            name: 'Email',
            value: '',
            pattern: /.+/
          },
          {
            name: 'Some Field 1',
            value: '',
            pattern: /.+/
          },
          {
            name: 'Some Field 2',
            value: '',
            pattern: /.+/
          }
        ]
      }
    },
    methods: {
      checkInput(e, key){

        console.log(e.target.value);

      }
    }
  }
</script>

<style scoped>
  .color-red {
    color: red;
  }

  .color-green {
    color: green;
  }
</style>
