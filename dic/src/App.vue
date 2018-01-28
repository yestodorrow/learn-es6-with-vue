<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单、易用、便捷</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm.vue'
import TranslateOutput from './components/TranslateOutput.vue'

export default {
  name: 'App',
  data(){
      return{
        translatedText:""
      }
  },
  components: {
    TranslateForm,
    TranslateOutput
  },
  methods:{
      translateText:function(text){
       this.$http.get("https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180128T153650Z.d7be1a2154af9c72.fa057669a0a84fd1a11d29636f722f200b74ce33&lang=en&text="+text).then((res)=>{
         this.tranlatedText=res.body.text[0];
         console.log(this.tranlatedText);
       })
      }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
