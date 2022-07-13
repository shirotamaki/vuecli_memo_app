<template>
    <span><button class="button" @click="openForm">+</button></span>
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