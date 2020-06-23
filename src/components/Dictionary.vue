<template>
  <div>
    <div v-for="letter in letterList" :key="letter"> 
      <Letter :letter="letter" :id="letter"/>
      <div class="layout">
        <div v-for="word in getWordsForLetter(letter)" :key="word.id">
          <WordCard :word="word" v-if="word.word[0] === letter"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import WordCard from './WordCard.vue'
import Letter from './Letter.vue'

export default {
  name: 'WordCard',
  props: ['words'],
  components: {
    WordCard,
    Letter
  },
  setup({ words }) {
    function generateLetterList () {
      const letters = [];
      for (let i = 0; i < words.length; i++) {
        const word = words[i];
        const wordLetter = word.word[0];
      
        if (letters.indexOf(wordLetter) === -1) {
          letters.push(wordLetter)
        }
      }
      return letters.sort()
    }

    function sortWords () {
      return words.sort(function(a, b) {
        return a.word.localeCompare(b.word);
      });
    }

    function getWordsForLetter (letter) {
      const wordsForLetter = [];
      for (let i = 0; i < words.length; i++) {
        const word = words[i];
        if (word.word[0] === letter) wordsForLetter.push(word)
      }

      return wordsForLetter;
    }

    return {
      words: sortWords(),
      letterList: generateLetterList(),
      getWordsForLetter
    }
  }
}
</script>

<style scoped lang="scss">
$breakpoint-phone: 640px;
$breakpoint-tablet: 768px;
$breakpoint-desktop: 1024px;

.dictionary {
  width: 100%;
  display: inline-block;
}
.layout {
  display: grid;
  align-items: center;
  grid-template-columns: 100%;
  padding: 20px;

  @media (min-width: $breakpoint-phone) {
    grid-template-columns: 50% 50%;
  }

  @media(min-width: $breakpoint-tablet) {
    grid-template-columns: 33% 33% 33%;
  }

  @media(min-width: $breakpoint-desktop) {
    grid-template-columns: 25% 25% 25% 25%;
  }
}

.content {
  width: 95%;
  float: left;
}

.nav {
  width: 5%;
  float: right;
}
</style>
