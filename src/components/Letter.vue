<template>
  <div class="letter-area">
    <div class="letter">{{ letter }}</div>
  </div>
</template>

<script>
export default {
  name: 'Letter',
  props: ['letter']
}
</script>

<style scoped>
.letter-area {
  display: flex;
  align-items: center;
  width: 150px;
  height: 50px;
  background-color: red;
  border: none;
}
.letter {
  color: white;
  text-transform: capitalize;
  font-weight: 600;
  font-size: 18px;
  padding-left: 20px;

  transform: scale(1);
  transition: 0.2s linear transform;
}

.letter:hover {
  transform: scale(1.4);
}
</style>