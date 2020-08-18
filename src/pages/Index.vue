<template>
  <q-page class="text-center tt">
    <h6 class="dd">Convert Numbers Between Any Bases.</h6>
<div class="q-ma-sm">
  <div class="q-ma-md">
 <!-- INPUT Base Number -->
    <q-input
      placeholder="Number To Convert"
      v-model.number="input"
      type="number"
      hint="Example 1110111"    
    />
  </div>
<div class="q-ma-md">
  <!-- INPUT Base Number-->
    <q-input
    placeholder="Inputbase"
      v-model.number="inputBase"
      type="number"
      hint="Example 2" 
    /> 
</div>
<div class="q-ma-md">
     <!-- OutPUT Base Number -->
    <q-input
    placeholder="Outputbase"
      v-model.number="outputBase"
      type="number"
      hint="Example 8"  
    />
</div>
<div class="q-mt-lg">
    <q-btn flat :disable="!input || !inputBase || !outputBase" class="full-width" @click="convertNumbers" color="white"  text-color="black" label="Convert" />

    <span v-show="!result.length">Hint: Each unit in the input number should be less than or equal the input base ..
</span>
</div>
<div v-show="false">
  <input type="text" v-model="result">
 
</div>

<div class="bbx" v-show="result.length">
  <!-- <h5>The Result is {{ result }}</h5> -->
  <h6 class="bb">Conversion from Base {{ inputBase }} to {{ outputBase }} is</h6>
  <br>
  <h6 class="bby"> {{ result }} </h6>
       <q-btn flat type="button"
      v-clipboard:copy="result"
      v-clipboard:success="onCopy"
      v-clipboard:error="onError">Copy To clipboard!</q-btn>
</div>
</div>
  </q-page>
</template>

<script>
import Vue from 'vue'
import VueClipboard from 'vue-clipboard2'
 
Vue.use(VueClipboard)

const { Convert } = require ('any-to-any');
export default {
  name: 'PageIndex',
  data (){
    return {
      input: '',
      inputBase: '',
      outputBase: '',
      result: ''
    }
  },
    methods: {
      convertNumbers(){
                this.$q.loading.show()
        setTimeout(() => {
          try {
             this.result = Convert(this.input, this.inputBase, this.outputBase ) 
                this.$q.loading.hide()
          } catch (error) {
        console.log(error)

                 this.$q.dialog({
        title: 'Error',
        message: 'You have an error.'
      }).onOk(() => {
        // console.log('OK')
      })
                this.$q.loading.hide()
                  this.input= '',
      this.inputBase= '',
      this.outputBase= ''

          }
         
        }, 1500);
        // console.log(this.result) 
      },
      onCopy: function (e) {
        this.$q.notify({
        message: 'Copied to clipboard.',
        color: 'green'
      })
    },
    onError: function (e) {
           this.$q.notify({
        message: 'Could not copy.',
        color: 'red'
      })
    }
      
    }
}
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Alata&display=swap');
.tt{
font-family: 'Alata', sans-serif;

}
.bb{
  /* border: 1px solid red; */
  margin: 25px 0 1px;
}
.bby{
  /* border: 1px solid red; */
  margin: 14px 0;
}
.dd{
  font-size: 25px;
  text-decoration: underline;
}

.bbx{
  /* border: 1px solid green; */
  margin-top: 10px;
}
</style>
