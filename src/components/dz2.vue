<template lang="pug">
  div
    .progress
      .progress-bar(role="progressbar" aria-valuenow="50" aria-valuemax="100" :style="progressCount" )

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
        progress: [0, 0, 0, 0, 0]
      }
    },
    methods: {
      checkValue(i) {
        let infoValue = this.info[i].value
        let infoPattern = this.info[i].pattern
        if (((infoValue) !== '') || (infoPattern.test(infoValue))) {
          this.classes.splice(i, 1, ((infoPattern.test(infoValue)) ? "fa-check-circle color-green" : "fa-exclamation-circle color-red"))
          this.progress.splice(i, 1, ((infoPattern.test(infoValue)) ? 1 : 0))

        } else {
          this.classes.splice(i, 1, '')
          this.progress.splice(i, 1, '')
        }

      }
    },
    computed: {
      buttonCheck() {
        return this.button = this.progress.reduce((a, b) => a + b, 0) !== this.classes.length

      },
      progressCount() {
        let sum = this.progress.reduce((a, b) => a + b)
        let length = this.progress.length

        // return this.status =  'width:' + sum / length * 100  + "%"
        return  {
          width: sum / length * 100  + "%"
        }

      }
    },
    beforeCreate() {
      console.log('bc');
      console.log(this.$el);
    },
    created() {
      console.log('c');
      console.log(this.$el);
    },
    beforeMount() {
      console.log('bm');
      console.log(this.$el);
    },
    mounted() {
      console.log('m');
      console.log(this.$el);
    },
    beforeUpdate() {
      console.log('bu');
      console.log(this.$el);

      // let pattern = /^[0-9]{7,14}$/;
      // let repPattern = /[^0-9]/g;
      // if(!pattern.test(this.info[1].value)) {
      //   this.info[1].value = this.info.value[1].replace(repPattern)
      // }
      // console.log( this.info[1])
    },
    updated() {
      console.log('u');
      console.log(this.$el);
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
