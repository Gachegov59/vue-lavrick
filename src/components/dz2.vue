<template lang="pug">
  div
    .progress
      .progress-bar(role="progressbar" aria-valuenow="50" aria-valuemax="100"  )

    form(@submit.prevent="formSubmited = true")

      .form-group.mb-1(v-for="(item, i) in info" :key="i")
        label {{item.name}} <i class="fas" :class="classes[i]"></i>
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
        classes: [],
        status: {
          width: 20
        }
      }
    },
    methods: {
       checkValue(i) {
          console.log('pattern test', this.info[i].pattern.test(this.info[i].value))
          console.log('pattern', this.info[i].pattern)
          console.log('value', this.info[i].value)
          console.log('i', i) //todo: есди заполнять не с первого косяк, вносит стил в первый

         if (((this.info[i].value) !== '') || (this.info[i].pattern.test(this.info[i].value))) {
           this.classes.splice(i, 1, ((this.info[i].pattern.test(this.info[i].value)) ? "fa-check-circle color-green" : "fa-exclamation-circle color-red" ))
           this.status.width +=  100 / this.info.length

         }
         else {
           this.classes.splice(i, 1, '')
           this.status.width -=  100 / this.info.length
         }
         console.log(this.classes)
         console.log(this.status.width)
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
