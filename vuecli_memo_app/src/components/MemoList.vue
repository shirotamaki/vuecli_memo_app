<template>
  <div>
    <ul>
      <li v-for="(memo, index) in memoList" :key="index">
        <span>{{ showTitle(memo) }}</span>
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
    }
  },
  methods: {
    showTitle (memo) {
      return memo.split(/\n/)[0]
    },
  }
}
</script>

<style>
</style>
