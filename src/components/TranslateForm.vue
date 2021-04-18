<template>
  <div id="TranslateForm">
      <form @submit.prevent="submitForm" class="form">
          <input
            name="content"
            type="text"
            v-model="textToTranslate"
            placeholder="Input your content here"
            class="input"
          />
          <label for="content">Input your content here</label>
          <select v-model="language">
              <option value="en">English</option>
              <option value="pl">Polish</option>
              <option value="ru">Russian</option>
              <option value="ja">Japanese</option>
          </select>
          <button type="submit">Translate</button>
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
