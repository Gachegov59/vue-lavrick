<template lang="pug">
  div
    .progress
      .progress-bar(role="progressbar" aria-valuenow="50" aria-valuemax="100" style="width: 0")

    form(@submit.prevent="formSubmited = true")

      .form-group.mb-1(v-for="(item, i) in info" :key="i")
        label {{item.name}} <i class="fas "></i>
          input( v-model="item.value"  v-on:change="checkValue(i)" )

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
        ],
        classes: []
      }
    },
    methods: {
       checkValue(i) {
          console.log(this.info[i].pattern.test(this.info[i].value))
         if ((this.info[i].value) !== '') {
           this.classes.push((this.info[i].pattern.test(this.info[i].value)) ? "fa-exclamation-circle" : 'fa-smile' )
         }
         else {
           this.classes.splice(i, 1)
         }
         console.log(this.classes)
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
