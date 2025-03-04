<template>
  <h2>Find synonyms</h2>
  <div class="search">
    <input v-model="word" placeholder="Write a word" />
    <BButton @click="fetchSynonyms">Get synonyms</BButton>
  </div>
  <ul v-if="synonymWords.length > 0">
    <li v-for="(synonymWord, index) in synonymWords" :key="index">{{ synonymWord }}</li>
  </ul>
  <p v-else-if="hasSearched">Can't find any synonyms for your word. Try another word.</p>
</template>
<script>
//v-for create html element and go through (loop) the label array and then show each synonyms in li, position in array is stored into index.
// :key makes each item unique and remember optimize performance
import axios from 'axios';

export default {
  data() {
    return {
      synonymWords: [],
      word: '',
      hasSearched: false,
      apiKey: 'EknBZIxOqPpM2nGidj40xw==EiTssydbGqgXalZJ',
      url: 'https://api.api-ninjas.com/v1/thesaurus?word=',
    };
  },
  methods: {
    fetchSynonyms() {
      this.hasSearched = true;
      const wordUrl = `${this.url}${this.word}`;

      axios
        .get(wordUrl, {
          headers: {
            'X-Api-Key': this.apiKey,
          },
        })
        .then((response) => {
          this.synonymWords = response.data.synonyms ;
          console.log(this.synonymWords);
        })
        .catch((error) => {
          console.error('Error', error);
          this.synonymWords = [];
        });
    },
  },
};
</script>
<style>
.todo-container {
  padding: 20px;
}
.search {
  padding: 20px;
}
li {
  justify-content: space-between;
  padding: 8px;
  border: 1px solid #ccc;
  margin-bottom: 5px;
}
ul {
    display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 300px));
    gap: 10px;
   list-style: none;
}
</style>
