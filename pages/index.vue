<template>
  <div class="container">
    <h2>Simple Deepl Translator</h2>
    <textarea placeholder="Write Here..." v-model="content" @input="translate"></textarea>
    <hr>
    <div class="result">
      <p>{{ result }}</p>
    </div>
  </div>
</template>

<style scoped>
  h2 {
    font-family: 'Roboto', sans-serif;
  }

  textarea {
      border: none;
      width: 800px;
      min-height: 200px;
      font-size: 1em;
      background : #f4f3ee;
      font-family: 'Roboto', sans-serif;
      font-weight: 100;
      padding: 10px;
      margin: 0;
      outline: none;
      resize: none;
    }

    .container {
      width: 100%;
      display: flex;
      align-items: center;
      flex-direction: column;
      justify-content: center;
    }

    .result {
      width: 800px;
      font-size: 1em;
      background : #f4f3ee;
      font-family: 'Roboto', sans-serif;
      font-weight: 100;
      padding: 10px;
      margin: 0;
    }
</style>

<script>
import axios from 'axios'

export default {
  name: 'IndexPage',
  data() {
    return {
      content :'',
      result: '',
      key: 'Your API Key',
    }
  },

  methods : {
    translate() {
      axios.get('https:api-free.deepl.com/v2/translate?auth_key='+ this.key +'&text=' + this.content + '&target_lang=FR')
           .then(response => (this.result = response.data.translations[0].text))
    }
  }
}
</script>
