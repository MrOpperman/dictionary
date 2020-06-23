<template>
  <div>
    <Dictionary v-if="words.length > 0" :words="words" />
    <div v-if="words.length === 0">Loading...</div>
  </div>
</template>

<script>
import { firestore } from '../firebase_config'

import Dictionary from './components/Dictionary.vue'

export default {
  name: 'App',
  components: {
    Dictionary
  },
  data: function () {
    return {
      words: []
    }
  },
  mounted: function () {
    const words = []
    const self = this;
    const dictionary = firestore.collection('dictionary').get()
      .then(res => res.docs)
      .then(docs => docs.forEach((doc, index) => {
        words.push({ id: index, ...doc.data() })
      }))
      .then(() => self.words = words)
  }
}
</script>
