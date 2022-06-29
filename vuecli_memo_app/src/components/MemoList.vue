<template>
  <div>
    <ul>
      <li v-for="(memo, index) in memoList" :key="index">
        <span @click="edit(index, memo)">{{ displayTitle(memo) }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['memoList'],

  data () {
    return {
      text: '',
      editIndex: -1,
      memos: [],
      inputMode: false,
    }
  },
  methods: {
    displayTitle (memo) {
      return memo.split(/\n/)[0]
    },
    edit (index, memo) {
      this.editIndex = index
      this.text = memo
      this.$emit('edit', this.editIndex, this.text)
    },
  },
}
</script>

<style>
</style>
