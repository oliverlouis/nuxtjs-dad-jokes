<template>
  <form @submit.prevent="submitForm">
    <input
      class="search-box"
      type="text"
      v-model="text"
      placeholder="Search jokes..."
    />
    <input class="btn" type="submit" value="Search Jokes" />
  </form>
</template>

<script>
export default {
  name: 'SearchJokes',

  data() {
    return {
      text: '',
    }
  },

  methods: {
    submitForm() {
      this.$emit('search-text', this.text)
      this.text = ''
    },
  },
}
</script>

<style scoped>
form {
  display: flex;
  margin: 0 20px;
  justify-content: space-between;
}
.search-box {
  padding: 0.5rem 1rem;
  border: none;
  border-bottom: 1px solid rgb(158, 157, 157);
  min-width: 400px;
  outline: none;
  transition: all 0.2s;
}

.search-box:focus {
  width: 420px;
  border-bottom: 1px solid rgb(37, 37, 37);
}

.btn {
  padding: 0.5rem 1rem;
  color: #fff;
  background-color: #333;
  border: none;
  cursor: pointer;
}

.btn:hover {
  background-color: rgb(12, 12, 12);
}

.btn:active {
  outline: none;
}
</style>