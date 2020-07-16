<template lang="pug">
  div
    .progress
      .progress-bar(role="progressbar" aria-valuenow="50" aria-valuemax="100" :style="progressWidth" )

    form(@submit.prevent="formSubmited = true")

      .form-group.mb-1(v-for="(item, i) in info" :key="i")
        label {{item.name}}
          span(v-if="controls[i].activated" :class="controls[i].error ?  'fas fa-exclamation-circle color-red' :'fas fa-check-circle color-green' ")
          input( :value="item.value"   @input="onInput(i, $event.target.value)")

      button.btn.btn-primary(:disabled="done < info.length") Send Data
      div {{done}}
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
            value: '223',
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
        controls: []
      }
    },
    beforeMount() {
      for (let i = 0; i < this.info.length; i++) {
        this.controls.push({
          error: !this.info[i].pattern.test(this.info[i].value),
          activated:this.info[i].value
        })
      }
    },
    methods: {
      onInput(index, value) {
        let data = this.info[index]
        let control = this.controls[index]

        data.value = value
        control.error = !data.pattern.test(value)
        control.activated = true;
      },
    },
    computed: {
      buttonCheck() {
        // return this.button = this.progress.reduce((a, b) => a + b, 0) !== this.classes.length
      },
      done() {
        let done = 0;

        for (let i = 0; i < this.controls.length; i++) {
          if (!this.controls[i].error) {
            done++;
          }
        }
        return done;
      },
      progressWidth() {
        return {
          width: (100 / this.controls.length * this.done) + '%'
        }
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
