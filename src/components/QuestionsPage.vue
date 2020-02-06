<template>
  <div class="questions-page">
    <div v-for="(questions, index) in info" :key="index">
      <a class="question" @click="showDetail(index)">{{ questions.question }}</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'QuestionsPage',

  props: {
    info: {
      type: Array,
      default: () => {},
    },
  },

  methods: {
    showDetail(index) {
      this.$emit('getIndex', index);
    },
  },

};
</script>

<style scoped lang="scss">
.questions-page {

  .question {
    padding: 20px;
    font-size: 18px;
    line-height: 22px;
    font-weight: 700;
    cursor: pointer;
    display: block;
    background-color: #F5F5F7;
    margin-bottom: 20px;
    text-align: center;
    transition: background-color 0.5s ease;

    &:hover {
      background-color: #d9d9d9;
    }
  }
}
</style>
