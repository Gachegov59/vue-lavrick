<template lang="pug">
  .container
    div(v-if="isShow")
      .text.mb-3(v-on:scroll="handleScroll") dolordolordolor ipsumipsumipsumipsumipsumipsumipsum dolordolordolordolor sit amet, consectetur adipisicing elit. Aut harum modi, placeat rem suscipit tempore voluptates! Amet deserunt, harum incidunt ipsa itaque magnam, modi nihil odit pariatur quidem quo sit. Ad commodi debitis delectus distinctio doloribus eos error eum facilis fuga fugiat fugit harum hic illum ipsa iure modi molestiae nemo neque nisi obcaecati officia, omnis optio pariatur perferendis porro quae qui quo recusandae reiciendis rem repellendus rerum sit suscipit tempora temporibus ullam voluptates? Consequuntur deleniti ea ex, exercitationem, explicabo harum iure molestias nam necessitatibus odio quidem quisquam quo quod vero voluptates. Alias aperiam at autem consequuntur cum delectus doloribus eligendi enim harum iusto libero magni minima modi nemo odio quibusdam quisquam repellendus sapiente, sed sint sit soluta tempora ut. Debitis deleniti dolore dolorem excepturi libero provident quas sed sunt ullam. Accusamus adipisci aliquid animi asperiores aspernatur atque aut blanditiis commodi consequatur doloribus et ex expedita fugiat illum ipsa, iste iusto magnam minima minus natus numquam odio perspiciatis placeat provident quam quas quibusdam quo repellendus reprehenderit tenetur totam unde velit veritatis vitae voluptas voluptates voluptatum. A ab aperiam consequuntur cupiditate dolor dolores esse facilis fugiat harum maxime, nihil nisi pariatur perferendis provident quidem quos repudiandae rerum sapiente similique tempore vero?

      .inputs.mb-3(v-if="scrollDown")
        .form-check.d-flex()
          label.form-check-label i agree this text
          input.form-check-input(type="checkbox" v-model="agree")
        .form-check.d-flex()
          label.form-check-label send me spam
          input.form-check-input(type="checkbox" v-model="sendSpam")
        div(v-if="sendSpam")
          .form-check.d-flex()
            label.form-check-label send me on email
            input.form-check-input(type="radio" value="email" v-model="spamTo" )
          .form-check.d-flex()
            label.form-check-label send me on phone
            input.form-check-input(type="radio" value="phone" v-model="spamTo")

      button.btn.btn-primary(v-if="agree" @click="isShowBlock") send data

    div(v-else="isShow")
      table.table(:class="flags")
        tbody
          tr
            td Agree text
            td yes
          tr
            td Get spam
            td {{approveSpam}}
          tr(v-if="sendSpam")
            td Spam on
            td {{spamTo}}
      button.btn.btn-primary(v-if="agree" @click="isShowBlock") send data
</template>

<script>
  export default {
    name: "dz2_2",
    data() {
      return {
        scrollDown: false,
        agree: false,
        isShow: true,
        sendSpam: false,
        spamTo: ''
      }
    },
    methods: {
      handleScroll(e) {
        if ( e.target.scrollHeight - e.target.scrollTop - e.target.offsetHeight < 10)
          this.scrollDown = true
        console.log(1)
      },
      isShowBlock() {
        this.isShow = !this.isShow
      }
    },
    computed:{
      approveSpam() {
        return this.sendSpam ? 'Yes' : 'No'
      }
    },
    created() {
      console.log(window.addEventListener('scroll', this.handleScroll))
    },
    destroyed() {
      console.log( window.removeEventListener('scroll', this.handleScroll))
    }

  }

</script>

<style scoped>
  .text {
    max-height: 300px;
    overflow: auto;
    overflow-x: hidden;
  }
</style>
