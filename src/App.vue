<template>
  <div id="app">
    <vue-autosuggest
    :suggestions="[{data:['Frodo', 'Samwise', 'Gandalf', 'Galadriel', 'Faramir', 'Éowyn']}]"
    :input-props="{id:'autosuggest__input', placeholder:'Do you feel lucky, punk?'}"
    @input="onInputChange"
    @selected="selectHandler"
    @click="clickHandler"
/>  
    
  </div>
</template>

<script>


export default {
  name: "App",
  components: {
  
  },
   methods:{
   onInputChange(){
     console.log('onInputChange')
   } ,
   selectHandler(){
     console.log('selectHandler')
},
clickHandler(){
     console.log('clickHandler')

}
  }
  
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
