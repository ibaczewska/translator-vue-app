<template>
  <div id="TranslateOutput" class="output">
      <h2>{translatedText}</h2>
  </div>
</template>

<script>

export default {
  name: 'TranslateOutput',
  props: {
    translatedText: {
      type: String
    }
  }
}
</script>

<style>

</style>
