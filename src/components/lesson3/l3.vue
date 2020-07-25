<template lang="pug">
  form
    h2 {{click}}
    hr
    button(v-ondelay:click.prevent="onClick").btn.btn-success send


</template>

<script>
  import Vue from "vue";

  Vue.directive('ondelay', {
    bind(el, options) {
      console.log(options)

      let callback = (e) => {
        if(options.modifiers.prevent) {
          e.preventDefault()
        }
        options.value.call(this, e);
        console.log(e)
      };

      el.addEventListener(options.arg, callback)
    }
  })

  export default {
    name: "lesson3",
    data() {
      return {
        click: 0,
      }
    },
    methods: {
      onClick() {
        this.click++
      }
    }
  }


</script>

<style scoped>

</style>
