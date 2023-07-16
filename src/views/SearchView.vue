<template>
  <!-- eslint-disable max-len -->
  <div class="wrapper">
    <ClaimComponent />
    <SearchInputComponent />
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import ClaimComponent from '@/components/ClaimComponent.vue';
import SearchInputComponent from '@/components/SearchInputComponent.vue';

const API = 'https://images-api.nasa.gov/search';
export default {
  name: 'SearchView',
  components: {
    ClaimComponent,
    SearchInputComponent,
  },
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
  margin: 0;
  padding: 30px;
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-image: url('../assets/heroimage.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 80% 0;
}

</style>
