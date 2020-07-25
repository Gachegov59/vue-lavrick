<template lang="pug">

  .form-group
    label {{name}}
    span.fa(v-if=activated  :class="validClass")
    input.form-control(type="text"  @input="onInput"
      :value="value")

</template>

<script>
  export default {
    props: ['name', 'value', 'pattern'],
    name: 'AppInput',
    data() {
      return {
        activated: this.value !== ''
      }
    },
    computed: {
      validClass() {
        return this.pattern.test(this.value) ?
          'fas fa-exclamation-circle text-success' :
          'fas fa-check-circle text-danger';
      }
    },
    methods: {
      onInput(e) {
        this.activated = true;
        this.$emit('changedata', {
          value: e.target.value,
          valid: this.pattern.test(e.target.value)
        })
      }
    }
  }
</script>
