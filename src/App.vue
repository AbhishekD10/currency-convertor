<template>
  <div id="app">
    <h1>Currency Converter</h1>
         <span>Enter Amount:</span><input type = "number" v-model.number = "amount" placeholder = "Enter Amount" /><br/><br/>
         <span>Convert From:</span>
         <select v-model = "convertfrom" style = "width:200px;font-size:25px;">
            <option v-for = "a in currencyfrom"  v-bind:value = "a.name">{{a.desc}}</option>
         </select>
         <span>Convert To:</span><select v-model = "convertto" style = "width:200px;font-size:25px;">
            <option v-for = "a in currencyfrom" v-bind:value = "a.name">{{a.desc}}</option>
         </select><br/><br/>
         <span> {{amount}} {{convertfrom}} equals {{finalamount}} {{convertto}}</span>
      
  </div>
</template>

<script>
export default {
data() {

  return{
               name:'',
               currencyfrom : [
                  {name:"USD", desc:"US Dollar"},
                  {name:"EUR", desc:"Euro"},
                  {name:"INR", desc:"Indian Rupee"},
               ],
               convertfrom: "INR",
               convertto:"USD",
               amount :"0"
            }},
            computed :{
               finalamount:function() {
                  var to = this.convertto;
                  var from = this.convertfrom;
                  var final;
                  switch(from) {
                     case "INR":
                     if (to == "USD") {
                        final = this.amount * 0.015;
                     }
                     if (to == "EUR") {
                        final = this.amount * 0.013;
                     }
                     if (to == "INR") {
                        final = this.amount;
                     }
                     break;
                     case "USD":
                     if (to == "INR") {
                        final = this.amount * 68.78;
                     }
                     if (to == "EUR") {
                        final = this.amount * 0.9;
                     }
                     if (to == "USD") {
                        final = this.amount;
                     }
                     break;
                     case "EUR":
                     if (to == "INR") {
                        final = this.amount * 76.67;
                     }
                     if (to == "USD") {
                        final = this.amount * 1.11;
                     }
                     if (to == "EUR") {
                        final = this.amount;
                     }
                     break;
                  }
                  return final;
               }
            }
}
</script> 

<style>
#app {
  padding: 20px 15px 15px 15px;
            margin: 0 0 25px 0;
            width: auto;
            background-color: lightblue;
}
span, option, input {
            font-size:25px;
         }
</style>
