<template>
  <div>
    <SearchJokes @search-text="searchText" />
    <Joke
      v-for="joke in jokes"
      :id="joke.id"
      :key="joke.id"
      :joke="joke.joke"
    />
  </div>
</template>

<script>
import axios from 'axios'
import Joke from '../../components/Joke'
import SearchJokes from '../../components/SearchJokes'
export default {
  components: {
    Joke,
    SearchJokes,
  },

  data() {
    return {
      jokes: [],
    }
  },

  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: 'application/json',
        },
      }

      try {
        const response = await axios.get(
          `https://icanhazdadjoke.com/search?term=${text}`,
          config
        )
        this.jokes = response.data.results
      } catch (error) {
        console.log(error)
      }
    },
  },

  async created() {
    const config = {
      headers: {
        Accept: 'application/json',
      },
    }

    try {
      const response = await axios.get(
        'https://icanhazdadjoke.com/search',
        config
      )
      this.jokes = response.data.results
    } catch (error) {
      console.log(error)
    }
  },

  head() {
    return {
      title: 'Dad Jokes',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Best place for corny dad jokes',
        },
      ],
    }
  },
}
</script>

<style scoped>
</style>