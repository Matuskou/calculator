<template>
  <div class="calc">
    <div class="input-container">
      
      <div>
        <input class="inFront"  placeholder=" "  v-model="number1"/>
        <input placeholder=" " v-model="number2"/>
        <input class="inBack" placeholder=" " v-model="myresult"/>
      </div>
      
    </div>

    <div class="buttons">
      <p></p>
        <button v-for="number of numbers" v-bind:key="number" :class="number">
        <Numbers v-bind:number="number" @buttonWasClicked="calOperation">
          
        </Numbers>
        
        </button>
    </div>
    
    <div class="number">
      <p></p>
      <button v-on:click="executePlus()">+</button>
      <button v-on:click="executeMinus()">-</button>
      <button v-on:click="executeMultiplication()">*</button>
      <button v-on:click="executeDivison()">/</button>
      <br>
      <button v-on:click="executeEquals()">=</button>
    </div>
    
    
  </div>
</template>

<script setup>


const number1 = ref("");
const number2 = ref("");
const myresult = ref(0);
const plus = ref(false);
const minus = ref(false);
const multiply = ref(false);
const divide = ref(false);

const executePlus=()=>{
  plus.value = true
}
const executeMinus=()=>{
  minus.value = true  
}
const executeMultiplication=()=>{
  multiply.value = true
}
const executeDivison=()=>{
  divide.value = true
}
const executeEquals=()=>{
  if (minus.value == true){
    myresult.value = +number1.value - +number2.value
  }
  else if (plus.value == true) {
    myresult.value = +number1.value + +number2.value
  }
  else if (multiply.value == true){
    myresult.value = +number1.value * +number2.value
  }
  else if (divide.value == true){
    myresult.value = +number1.value / +number2.value
  }
}


const numbers = ref([
  {value: "1"},
  {value: "2"},
  {value: "3"},
  {value: "4"},
  {value: "5"},
  {value: "6"},
  {value: "7"},
  {value: "8"},
  {value: "9"},
  {value: "0"}

])

function calOperation (number){
  let selectedNumber = numbers.value.find(item => item == number)
  if (plus.value == true || minus.value == true || divide.value == true || multiply.value == true){
    number2.value += selectedNumber.value
  }else{
    number1.value += selectedNumber.value
  }
}

</script>
<style>

.number{
  font-size: 20px;
  margin-left: 2px;
  margin-right: 2px;
  border-radius: 50%;

}

.input-container{
  display: flex;
  align-items: center;
  width: 100%;
  max-height: 65px;
}

body{

  background: linear-gradient(to right bottom, rgb(130, 211, 234), rgb(2, 59, 61));
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;

}

.calculator{
  
  padding: 20px;
  padding-bottom: 200px;
  
  background-color: #947878;
  border-radius: 10px;
  margin:auto;

}
input{
  font-weight: bold;
  display: center;
  justify-content: center;
  align-items: center;
  row-gap: 12px;
  font-family: 'Orbitron', sans-serif;
  background:linear-gradient(to right bottom, rgba(124, 124, 124, 0.849), rgb(58, 58, 58));
  color: black;
  border: solid  0.5px;
  max-width: 104px;
  border-color: rgba(124, 124, 124, 0.849);
  height: 10%;
  font-size: 15px;
  margin-bottom: 5px;
  text-align: center;
}
.inFront{
  border-radius: 10% 0% 0% 10%;
}
.inBack{
  border-radius: 0% 10% 10% 0%
}
.buttons{
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  justify-content: space-around;
  height: 10px;
}
button{
  background: linear-gradient(to right bottom, rgba(124, 124, 124, 0.849), rgb(58, 58, 58)) ;
  color: rgb(0, 0, 0);
  border-radius: 10%;
  border-color: rgba(124, 124, 124, 0.849);
}
.table{
  width: 30%;
  height: 100px;
  float: bottom;
  margin: 10px;
  
}
</style>