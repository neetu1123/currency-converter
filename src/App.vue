<script setup >
import { computed, ref } from "vue";
import { useCounterStore } from "@/stores/counter";
const store = useCounterStore();

const selectedOne = ref(""); // for base currency selected (from)
const selectedTwo = ref(""); // for 2nd currency  option selected  (to)
const inputOne = ref(); // bind the property with input one
const inputTwo = ref(); // bind the property with input two

//function for check the value for selcetedOne and selectedTwo value
function converterBtn() {
    let i = ref('');
    let j = ref('');
    
    let amount = ref(1);
    if (selectedOne.value in store.currency) {
      i = selectedOne.value;
      if (selectedTwo.value in store.currency) {
        j = selectedTwo.value;
        
        amount = store.currency[i][j];
        amount = amount * inputOne.value;
        inputTwo.value = amount;
        console.log(amount)
      }
    }
  }
</script>

<template>
  <div class="current">

    <span>{{ inputTwo }}</span>
    <small>Currency converter app</small>
  </div>
  <!-- for first select option  -->
  <div class="select">
    <select v-model="selectedOne" @click="selectValueOne">
      <option disabled value="">Select currency</option>
      <option value="KD">Kuwaiti Dinar</option>
      <option value="BD">Bahraini Dinar</option>
      <option value="OMRL">Omani Rial</option>
      <option value="BPS">British Pound Sterling</option>
      <option value="EER">European Euro</option>
      <option value="USD">US Dollor</option>
      <option value="BDR">Brunei Dollor</option>
      <option value="NZD">New Zealand Dollor</option>
      <option value="AF">Aruban Florin</option>
      <option value="INR">Indian Rupee</option>
    </select>
  </div>
  <!-- for second select option -->
  <div class="select">
    <select v-model="selectedTwo" @click="selectValueTwo">
      <option disabled value="">Select currency to convert</option>
      <option value="KD">Kuwaiti Dinar</option>
      <option value="BD">Bahraini Dinar</option>
      <option value="OMRL">Omani Rial</option>
      <option value="BPS">British Pound Sterling</option>
      <option value="EER">European Euro</option>
      <option value="USD">US Dollor</option>
      <option value="BDR">Brunei Dollor</option>
      <option value="NZD">New Zealand Dollor</option>
      <option value="AF">Aruban Florin</option>
      <option value="INR">Indian Rupee</option>
    </select>
  </div>
  <br />
  <!-- first input in this we can  fill the number you want to convert in other currrency -->
  <div class="inputOne">
    <input type="number" v-model="inputOne" />
  </div>
  <!-- second input in this we have to see the result(change the currency )  -->
  <div class="inputTwo">
    <input type="number" v-model="inputTwo" />
  </div>
  <!-- button with click event when we click then it's perform the action and with the help of convertBtn function -->
  <div>
    <button @click="converterBtn">converter button</button>
  </div>
   
</template>

<style >

.select {
  display: inline-block;
  align-content: center;
}
.inputOne,
.inputTwo {
  display: inline-block;
  margin: 10px;
}
#app {
  align-content: center;
}
.current {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 200px;
  height: 200px;
  text-align: center;
  background-color: white;
  border-radius: 999px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  border: 5px solid hwb(330 41% 0%);
  margin: 0 auto 2rem;
}
.current span {
  display: block;
  font-size: 2em;
  font-weight: bold;
  margin-bottom: 0.5rem;
}
.current small {
  color: rgb(53, 49, 49);
  font-style: italic;
  font-weight: bold;
  padding: 10px;
  
}
</style>
