<template>
  <div id="app" class="container">
    <translate-form @formSubmit="textTranslate"/>
    <translate-output v-text="translatedText"/>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

const BASE_URL = 'https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20200128T194200Z.1b739b8442cf57bf.bb2cc42377ef5e37004f61fb7067376ab53c35a4&lang='

export default {
  name: 'app',
  data () {
    return {
      translatedText: '',
      image: './assets/background.jpg'
    }
  },

  components: {
    TranslateForm,
    TranslateOutput
  },
  methods: {
    textTranslate (text, language) {
      this.$http.get(BASE_URL + language + '&text=' + text)
        .then((res) => {
          this.translatedText = res.body['text'][0]
        })
    }
  }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  background: url('../src/assets/background.jpg') center;
  background-size: cover;
  background-repeat: no-repeat;
  margin: 0;
  padding: 0;

}

.container {
  height: 100%;
  min-height: 100vh;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: rgba(255,255,255,0.5);

}
</style>
