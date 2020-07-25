
<template lang="pug">
  div
    .container
      form(@submit.prevent="formSubmited = true" v-if="!formSubmited")
        .progress
          .progress-bar(:style="progressWidth")

        AppInput(v-for="(item, index) in info"
          :name="item.name"
          :value="item.value"
          :pattern="item.pattern"
          :key="index"
          @changedata="onChangeData(index, $event)")

        button.btn.btn-primary(:disabled="done < info.length")
          Send Data
      <div v-else>
        <table class="table table-bordered">
          <tr v-for="(item, index) in  info">
            <td>{{ item.name }}</td>
            <td>{{ item.value }}</td>
          </tr>
        </table>
      </div>
</template>

<script>
  import Dz2 from "./components/lesson1/dz2.vue";
  import Dz2_2 from "./components/lesson1/dz2_2.vue";
  import styles from "./components/lesson1/styles.vue";
  import styles2 from "./components/lesson1/styles2.vue";
  import lesson3 from "./components/lesson3/l3.vue";
  import appSome from "./components/lesson3/appSome.vue";
  import AppInput from "./components/lesson4/Input.vue";

  console.log("appSome",appSome.data)

  export default {
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
        controls: [],
        done: 0,
        formSubmited: false
      }
    },
    components: {
      Dz2: Dz2,
      Dz2_2: Dz2_2,
      Styles: styles,
      Styles2: styles2,
      lesson3: lesson3,
      appSome: appSome,
      AppInput
    },
    methods: {
      onChangeData(index, data){
        this.info[index].value = data.value;
        this.controls[index] = data.valid;

        let done = 0;

        for(let i = 0; i < this.controls.length; i++){
          if(this.controls[i]){
            done++;
          }
        }

        this.done = done;
      }

    },
    computed: {
      progressWidth(){
        return {
          width: (this.done / this.info.length * 100) + '%'
        }
      }
    }

  }
</script>

<style>
  .container {
    max-width: 600px;
    margin: auto;
  }

  input {
    width: 100%;
    max-width: 400px;
  }
</style>

