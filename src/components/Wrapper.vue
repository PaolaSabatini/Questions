<template>
  <div class="wrapper">

    <span @click="addQuestionOpen()">Send a question</span>

    <AddQuestions v-if="this.formVisible"/>

    <QuestionsPage
      v-if="!this.isVisible"
      :info="info"
      v-on:getIndex="getQuestion($event)"/>

    <DetailsPage
      v-if="this.isVisible"
      :infoQuestion="info[this.questionIndex]"
      v-on:goBack="updateVisibility($event)"/>

  </div>
</template>

<script>
import axios from 'axios';

import AddQuestions from './AddQuestions.vue';
import QuestionsPage from './QuestionsPage.vue';
import DetailsPage from './DetailsPage.vue';

export default {
  name: 'Wrapper',

  components: {
    AddQuestions,
    QuestionsPage,
    DetailsPage,
  },

  data() {
    return {
      info: [],
      questionIndex: '',
      isVisible: false,
      formVisible: false,
    };
  },

  mounted() {
    axios
      .get('https://polls.apiblueprint.org/questions?10')
      .then((response) => { this.info = response.data; });
  },

  methods: {

    getQuestion(index) {
      this.questionIndex = index;
      this.isVisible = true;
    },

    updateVisibility() {
      this.isVisible = false;
    },

    addQuestionOpen() {
      this.formVisible = !this.formVisible;
    },
  },

};
</script>

<style lang='scss'>
.wrapper {
  display: flex;
  justify-content: center;
  padding: 140px 20px 10px 20px;

  span {
    position: fixed;
    top: 0;
    left: 0;
    color: white;
    padding: 70px 0 0 20px;
    z-index: 2;
    cursor: pointer;

    &:hover {
      font-weight: 700;
    }
  }
}

</style>
