<template>
  <div class="claimWrapper">
    <h1 class="claim">SPACER</h1>
    <p class="subclaim">
        Begin your journey through our amazing galaxy, and discover places you never even heard of.
    </p>
    <p class="subclaim">
        Type anything space-related to start.
    </p>
  </div>
</template>

<script>
export default {
  name: 'ClaimComponent',
};
</script>

<style lang="scss" scoped>
.claimWrapper {
    display: flex;
    text-align: center;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: white;
}
.claim {
  margin: 0;
  font-size: 5rem;

  @media (min-width: 768px) {
    font-size: 8rem;
  }
  @media (min-width: 992px) {
    font-size: 10rem;
  }
}

.subclaim {
  margin: 20 px 0 0 0 ;
  font-size: 1.3rem;
  font-weight: 300;
  @media (min-width: 768px) {
    width: 600px;
    font-size: 2rem;
    line-height: 1;
    letter-spacing: 1px;
  }
}
</style>
