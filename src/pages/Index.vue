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
    <q-btn class="full-width" @click="convertNumbers" color="white"  text-color="black" label="Convert" />

</div>
<div class="bbx" v-show="result.length">
  <!-- <h5>The Result is {{ result }}</h5> -->
  <h6 class="bb">Your Result is:</h6>
  <br>
  <h6 class="bby">****** {{ result }} ******</h6>
</div>
</div>
  </q-page>
</template>

<script>

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
        this.result = Convert(this.input, this.inputBase, this.outputBase )
        // console.log(this.result) 
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
  margin: 0;
}
.bby{
  /* border: 1px solid red; */
  margin: 0;
}
.dd{
  text-decoration: underline;
}

.bbx{
  /* border: 1px solid green; */
  margin-top: 10px;
}
</style>
