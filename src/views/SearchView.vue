<template>
  <!-- eslint-disable max-len -->
  <div class="wrapper">
    <div class="search">
      <label for="search"
        >Search
        <input
          id="search"
          name="search"
          placeholder="e.g. Titan"
          v-model="searchValue"
          @input="handleInput"
        />
      </label>
      <ul>
        <li v-for="item in results" :key="item.data[0].nasa_id">
          <p>{{ item.data[0].description }}</p>

        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search';
export default {
  name: 'SearchView',
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: debounce(function () {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`).then((response) => {
        this.results = response.data.collection.items;
      }).catch((error) => {
        console.log(error);
      });
    }, 500),
  },
};
</script>
<style lang="scss" scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0;
  padding: 30px;
  width: 100%;
}

.search {
  display: flex;
  flex-direction: column;
  width: 250px;
}

input {
  height: 40px;
  border: 0;
  border-bottom: 1px solid black;
}
label {
  font-family: Montserrat, sans-serif;
}
</style>
