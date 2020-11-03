<template>
  <div class="hello">
    <input type='text' v-model='state.num1'>
    <span>+</span>
    <input type='text' v-model='state.num2'>
    <span>=</span>
    {{state.result}}
    <button type='button' @click='clickEvent()'>emit event:</button>
  </div>
</template>

<script>


import {reactive, computed} from 'vue'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  // 没有this
  setup(props, { emit }){
      console.log('setup > props', props);

    const state = reactive({
      num1: 0,
      num2: 0,
      result: computed(() => parseInt(state.num1) + parseInt(state.num2))
    })

    const clickEvent = () => {
      emit("sendmsg", state.result)
    }

    return {
      state,
      clickEvent
    }
  },
  // data () {
  //   return {
  //     num1: 0, 
  //     num2: 0,
  //     result: 0
  //   }
  // },
  // computed: {
  //   result(){
  //     return parseInt(this.num1) + parseInt(this.num2)
  //   }
  // },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
