<template>
  <div class="header">
    <h1>{{ title }}</h1>
  </div>
</template>

<script>

export default {
  name: 'Header',

  props: {
    title: {
      type: String,
      default: 'questions.',
    },
  },

  methods: {

    openForm() {
      this.$emit('openForm', true);
    },

  },

};
</script>

<style lang="scss">
  .header {
    top: 0;
    left: 0;
    background-color: black;
    text-align: end;
    position: fixed;
    width: 100%;
    z-index: 1;
    display: flex;
    justify-content: flex-end;

    h1 {
      color: white;
      margin: 0;
      padding: 30px 0 30px 30PX;
    }

  }

</style>
