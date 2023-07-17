<!-- eslint-disable max-len -->
<template>
  <div :class="[{ flexStart: step === 1 },'wrapper']">
    <transition name="slide">
      <img src="./assets/logo.svg" alt="logo" class="logo" v-if="step === 1">
    </transition>
    <transition name="fade">
      <HeroImageComponent v-if="step === 0" />
    </transition>
    <ClaimComponent v-if="step === 0" />
    <SearchInput v-model="searchValue" @input="handleInput" :dark="step === 1" />
    <div class="results" v-if="results && !loading && step === 1">
      <ItemComponent v-for="item in results" :item="item" :key="item.data[0].nasa_id"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import ClaimComponent from './components/ClaimComponent.vue';
import SearchInput from './components/SearchInput.vue';
import HeroImageComponent from './components/HeroImageComponent.vue';
import ItemComponent from './components/ItemComponent.vue';

const API = 'https://images-api.nasa.gov/search';
// console.log(this.searchValue);
export default {
  name: 'App',
  components: {
    ClaimComponent,
    SearchInput,
    HeroImageComponent,
    ItemComponent,
  },
  data() {
    return {
      loading: false,
      step: 0,
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: debounce(function () {
      console.log(this.searchValue);
      this.loading = true;
      axios.get(`${API}?q=${this.searchValue}&media_type=image`).then((response) => {
        this.results = response.data.collection.items;
        this.loading = false;
        this.step = 1;
      }).catch((error) => {
        console.log(error);
      });
    }, 500),
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;800&display=swap');

* {
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
html {
  font-size: 62.5%;
}
body {
  font-family: 'Montserrat', sans-serif;
  margin: 0;
  padding: 0;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .3s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
.slide-enter-active, .slide-leave-active {
  transition: all .3s ease;
}
.slide-enter-from, .slide-leave-to {
  margin-top: -50px;
}
.wrapper {
  position: relative;
  margin: 0;
  padding: 30px;
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  &.flexStart {
    justify-content: flex-start;

  }
}
.logo {
  position: absolute;
  top: 30px;
}

</style>
