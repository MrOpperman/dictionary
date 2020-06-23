<template>
  <div class="word-card">
    <div>
      <span class="word">{{word.word}}</span> <span>({{word.pronunciation}})</span> <span class="part-of-speech">{{word.part_of_speech}}</span>
    </div>
    <div class="subtext">
       <span v-if="word.gender">[{{ word.gender }}]</span>
    </div>
    {{ word.description }}
  </div>
</template>

<script>
export default {
  name: 'WordCard',
  props: ['word']
}
</script>

<style scoped>
.word-card {
  margin-top: 16px;
  margin-bottom: 16px;
}
.word {
  font-weight: 600;
  text-transform: capitalize;
  font-size: 18px;
}
.part-of-speech {
  font-style: italic;
  text-transform: capitalize;
}
.subtext {
  font-size: 14px;
  padding-top: 4px;
  padding-bottom: 4px;
}
</style>