<template>
  <div class="details-page">
    <a class="ricon-arrow_back" @click="goBack()"></a>
    <p class="question-detail">
      {{infoQuestion.question}}
    </p>
    <ul>
      <li class="choices" v-for="(choices, index) in infoQuestion.choices" :key="index">
        {{choices.choice}}
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'DetailsPage',

  props: {
    infoQuestion: {
      type: Object,
      default: () => {},
    },
  },

  methods: {

    goBack() {
      this.$emit('goBack', false);
    },

  },

};
</script>

<style lang="scss">
.details-page {
  display: flex;
  justify-content: center;
  flex-direction: column;
  position: relative;
  min-width: 40%;

  a {
    display: inline-block;
    padding-bottom: 20px;
    cursor: pointer;

    &:hover {
      transform: translate(-10px);
    }
  }

  ul {
    padding: 0 40px;
  }

  .question-detail {
    position: relative;
    padding: 20px;
    font-size: 18px;
    line-height: 22px;
    font-weight: 700;
    display: block;
    background-color: #888;
    margin: 0px 20px 20px 20px;
    text-align: center;
  }

  .choices {
    list-style: none;
    background-color: #F5F5F7;
    padding: 10px;
    margin-bottom: 10px;
    text-align: center;
    cursor: pointer;
    transition: background-color 0.5s ease;

    &:hover {
      background-color: #d9d9d9;
    }
  }

  .ricon-arrow_back:before {
    content: "\e903";
    font-size: 24px;
    font-weight: 700;
  }
}
</style>
