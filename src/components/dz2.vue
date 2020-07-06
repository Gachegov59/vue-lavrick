<template lang="pug">
  div
    .progress
      .progress-bar(role="progressbar" aria-valuenow="50" aria-valuemax="100" :style=`{width: progressCount + "%"}` )

    form(@submit.prevent="formSubmited = true")

      .form-group.mb-1(v-for="(item, i) in info" :key="i")
        label {{item.name}} <i class="fas" :class="classes[i]"></i>
          input( v-model="item.value"  v-on:change="checkValue(i)" )

      button.btn.btn-primary(:disabled="buttonCheck") Send Data
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
        classes: ['', '', '', '', ''],
        progress: [0, 0, 0, 0, 0],
        status: 0
      }
    },
    methods: {
      checkValue(i) {
        if (((this.info[i].value) !== '') || (this.info[i].pattern.test(this.info[i].value))) {
          this.classes.splice(i, 1, ((this.info[i].pattern.test(this.info[i].value)) ? "fa-check-circle color-green" : "fa-exclamation-circle color-red"))
          this.progress.splice(i, 1, ((this.info[i].pattern.test(this.info[i].value)) ? 1 : 0))

        } else {
          this.classes.splice(i, 1, '')
          this.progress.splice(i, 1, '')
        }

      }
    },
    computed: {
      buttonCheck() {
        return this.button = this.progress.reduce((a, b) => a+ b, 0) !== this.classes.length

      },
      progressCount() {
        let sum = this.progress.reduce((a, b) => a+ b)
        let length = this.progress.length

        return this.status = sum / length * 100

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
