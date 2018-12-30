<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单、易用、便捷</h5>
 <TranslateForm v-on:formSubmit="translateText">
 </TranslateForm>
    <br>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
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
    TranslateForm,TranslateOutput
  },
  methods: {
    translateText: function (Text,lg) {
//      alert(Text)
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181230T054036Z.4b25e172758a6b59.849dba7d4298e29d0ec9aae4429f46d7b958b6ae&lang='+lg+'&text=' + Text).then((response) => {
//        console.log(response.body.text[0])
         this.translatedText = response.body.text[0]
      });
    }
  }
};
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
