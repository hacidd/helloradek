<template>
  <div :style="style" class="item"></div>
</template>
<script>
export default {
  name: 'ItemComponent',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      photo: this.item.links[0].href,
      title: this.item.data[0].title,
      style: {
        backgroundImage: `url("${this.photo}")`,
      },
    };
  },
};
</script>
<style lang="scss" scoped>
.item {
  width: 300px;
  height: 300px;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: 50%;
}
</style>
