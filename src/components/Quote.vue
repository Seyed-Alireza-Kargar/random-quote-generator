<template>
  <div>
    <div v-if="loading" class="loading">Loading...</div>
    <div v-if="quote" class="quote">
      <p>{{ quote.content }}</p>
      <p>- {{ quote.author }}</p>
      <p>{{ quote.dateAdded }}</p>
      <p>tags :</p>
      <div v-for="(tag, index) in quote.tags" :key="index">
        <p>{{ index + 1 }} - <span>#{{ tag.replace(' ', '_') }}</span></p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'RandomQuote',
  data() {
    return {
      quote: null,
      loading: true
    };
  },
  async created() {
    try {
      const response = await axios.get('https://api.quotable.io/random');
      this.quote = response.data;
      this.loading = false;
    } catch (error) {
      console.error('Error fetching quote:', error);
    }
  }
};
</script>

<style>
.loading {
  font-size: 18px;
  font-style: italic;
  color: gray;
}

.quote {
  font-size: 24px;
}
</style>
