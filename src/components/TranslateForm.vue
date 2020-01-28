<template>
  <div id="TranslateForm">
      <form @submit.prevent="submitForm">
          <input type="text" v-model="textToTranslate" placeholder="Input your content here"/>
          <select v-model="language">
              <option value="en">English</option>
              <option value="pl">Polish</option>
              <option value="ru">Russian</option>
              <option value="ja">Japanese</option>
          </select>
          <input type="submit" value="Translate">
      </form>
  </div>
</template>

<script>

export default {
  name: 'TranslateForm',
  data: function () {
    return {
      textToTranslate: '',
      language: 'en'
    }
  },

  methods: {
    submitForm (e) {
      this.$emit('formSubmit', this.textToTranslate, this.language)
    }
  }
}
</script>

<style>

</style>
