<template>
  <div class="memo-list">
    <ul class="memo-list-ul">
      <li v-for="(memo, index) in memoList" :key="index" class="memo-text">
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
.memo-list {
  margin:0 auto;
}

.memo-list-ul {
  margin: 0;
  list-style: none;
  padding-left: 8px;
}

.memo-text:hover {
  color: blue;
  text-decoration: underline;
}
</style>
