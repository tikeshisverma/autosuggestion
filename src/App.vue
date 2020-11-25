<template>
  <div id="app">
  <pre v-if="selected">You have selected: '{{selected}}'</pre>
   <vue-autosuggest :suggestions="filteredOptions" :on-selected="onSelected" :limit="10" :input-props="inputProps"></vue-autosuggest>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
      return {
        selected: '',
        options: [{
          data: ['Tata', 'Reliance', 'L&T', 'Yes Bank', 'M&M', 'H&M', 'MRF', 'Maruti', 'Cipla']
        }],
        filteredOptions: [],
        inputProps: {
          id: "autosuggest__input",
          onInputChange: this.onUserInput,
          placeholder: "Type 'T'"
        },
        limit: 10
      };
    },
    methods: {
      onSelected(option) {
          this.selected = option.item;
      },
      onUserInput(text) {
        if (text === '' || text === undefined) {
          return;
        }
        
        /* Full control over filtering. Maybe fetch from API?! Up to you!!! */
        const filteredData = this.options[0].data.filter(item => {
          return item.toLowerCase().indexOf(text.toLowerCase()) > -1;
        }).slice(0, this.limit);
        
        this.filteredOptions = [{
          data: filteredData
        }];
      }
    }
  
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
    body {
      max-width: 800px;
      padding: 20px;
      margin-left: auto !important;
      margin-right: auto !important;
      font-family: monospace;
    }
    
    #autosuggest__input {
      outline: none;
      position: relative;
      display: block;
      font-family: monospace;
      font-size: 20px;
      border: 1px solid #616161;
      padding: 10px;
      width: 100%;
      box-sizing: border-box;
      -webkit-box-sizing: border-box;
      -moz-box-sizing: border-box;
    }
    
    #autosuggest__input.autosuggest__input-open {
      border-bottom-left-radius: 0;
      border-bottom-right-radius: 0;
    }
    
    .autosuggest__results-container {
      position: relative;
      width: 100%;
    }
    
    .autosuggest__results {
      font-weight: 300;
      margin: 0;
      position: absolute;
      z-index: 10000001;
      width: 100%;
      border: 1px solid #e0e0e0;
      border-bottom-left-radius: 4px;
      border-bottom-right-radius: 4px;
      background: white;
      padding: 0px;
      overflow: scroll;
      max-height: 200px;
    }
    
    .autosuggest__results ul {
      list-style: none;
      padding-left: 0;
      margin: 0;
    }
    
    .autosuggest__results .autosuggest__results_item {
      cursor: pointer;
      padding: 15px;
    }
    
    #autosuggest ul:nth-child(1) > .autosuggest__results_title {
      border-top: none;
    }
    
    .autosuggest__results .autosuggest__results_title {
      color: gray;
      font-size: 11px;
      margin-left: 0;
      padding: 15px 13px 5px;
      border-top: 1px solid lightgray;
    }
    
    .autosuggest__results .autosuggest__results_item:active,
    .autosuggest__results .autosuggest__results_item:hover,
    .autosuggest__results .autosuggest__results_item:focus,
    .autosuggest__results .autosuggest__results_item.autosuggest__results_item-highlighted {
      background-color: #ddd;
    }

</style>
