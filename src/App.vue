<template>
  <div id="app">
    <translate-form @formSubmit="textTranslate"/>
    <translate-output v-text="translatedText"/>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  data () {
    return {
      translatedText: ''
    }
  },

  components: {
    TranslateForm,
    TranslateOutput
  },
  methods: {
    textTranslate (text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20200128T194200Z.1b739b8442cf57bf.bb2cc42377ef5e37004f61fb7067376ab53c35a4&lang=' + language + '&text=' + text).then((res) => {
        this.translatedText = res.body['text'][0]
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
