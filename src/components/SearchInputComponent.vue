<template>
<div class="searchWrapper">
  <div class="search">
      <input
          id="search"
          name="search"
          v-model="searchValue"
          @input="handleInput"
        />
      <ul>
        <li v-for="item in results" :key="item.data[0].nasa_id">
          <p>{{ item.data[0].description }}</p>

        </li>
      </ul>
    </div>
</div>
</template>

<script>
export default {
  name: 'SearchInputComponent',
};
</script>

<style lang="scss" scoped>

.searchWrapper {
  margin-top: 50px;
  display: flex;
  flex-direction: column;
  text-align: center;
  width: 250px;

  input {
  height: 40px;
  border: 0;
  background: none;
  border-bottom: 1px solid black;
 }
}

</style>
