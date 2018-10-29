<template>
  <div class="container text-center" id="app">
      <h1>Word Translator</h1>
      <h5>Menggunakan Vue.js</h5>
      <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
      <TranslateOutput v-text="translatedText"></TranslateOutput>

  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  components:{
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return{
      translatedText:''
    }
  },
  methods:{
    translateText: function(text,language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181029T053643Z.c9267ca9dc24f7b6.6c16349ec84c8ef719213e6528aa485b96974e23&lang='+language+'&text='+text).then((response)=>{
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
body {
  background:#fefefe;
}
</style>
