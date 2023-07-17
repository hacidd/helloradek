<template>
      <input
          id="search"
          name="search"
          :class="{ dark : dark }"
          :value="value"
          @input="handleChange"
        />
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      // default: 'iss',
      required: true,
    },
    dark: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
  input {
    margin-top: 50px;
    display: flex;
    flex-direction: column;
    width: 250px;
    color: white;
    height: 40px;
    border: 0;
    font-size: 2rem;
    text-align: center;
    background: none;
    border-bottom: 1px solid white;
    transition: box-shadow .3s ease-out;

    @media(min-width: 992px) {
      font-weight: 400;
    }
  }
  input:focus,input:hover {
   outline: none;
   box-shadow: 0 10px 12px -8px rgba(255,255,255, .5);
  }
  .dark {
    color: #1e3d4a;
    border-bottom-color: #1e3d4a;
  }
  .dark:focus {
    box-shadow: 0 10px 12px -8px rgba(#1e3d4a, .5);
  }

</style>
