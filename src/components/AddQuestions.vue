<template>
  <div class="add-questions">
    <form @submit="formSubmit">
      <input type="text" class="question" v-model="question" placeholder="Question:">
      <input class="choices" placeholder="Choice 1" v-model="choice1">
      <input class="choices" placeholder="Choice 2" v-model="choice2">
      <input class="choices" placeholder="Choice 3" v-model="choice3">
      <button class="submit-button">Submit</button>
    </form>
      <span>
        {{output}}
      </span>
  </div>
</template>

<script>
export default {
  name: 'AddQuestions',

  data() {
    return {
      question: '',
      choices: [],
      choice1: '',
      choice2: '',
      choice3: '',
      output: '',
    };
  },

  methods: {
    formSubmit(e) {
      this.choices = [this.choice1, this.choice2, this.choice3];

      e.preventDefault();
      const currentObj = this;
      this.axios.post('https://polls.apiblueprint.org/questions?1', {
        question: this.question,
        choices: this.choices,
      })
        .then(() => {
          currentObj.output = 'Send It!';
        })
        .catch((error) => {
          currentObj.output = error;
          console.log('error', error);
        });
    },
  },
};
</script>

<style lang="scss">
  .add-questions {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    flex-wrap: wrap;
    background-color: rgba(0, 0, 0, 0.6);
    left: 0px;
    top: 100px;
    padding: 30px 0;
    position: fixed;
    z-index: 2;

    .question,
    .choices {
      background-color: white;
      border: none;
      padding: 10px;
      margin: 10px;
    }

    .submit-button {
      padding: 5px 10px;
      border: none;
      min-width: 100px;
      cursor: pointer;
      font-size: 15px;

      &:hover {
        background-color: #888;
        font-weight: 700;
      }
    }

    span {
      padding: 10px;
      font-weight: 700;
      font-size: 20px;
    }
  }

  @media screen and (max-width: 1024px) {
    .add-questions {
      form {
        display: flex;
        flex-direction: column;
        justify-content: center;

        .submit-button {
          width: 100%;
          margin-top: 20px;
        }
      }
    }
  }

</style>
