<template>
  <form @submit.prevent>
    <span><button class="button" @click="openForm" type="submit">+</button></span>
  </form>
</template>

<script>
export default {
  methods: {
    openForm () {
      this.$emit('open')
    },
  }
}
</script>

<style scoped>
.button {
  margin: 8px 0px 8px 8px;
}
</style>