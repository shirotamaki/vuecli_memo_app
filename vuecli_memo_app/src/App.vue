<template>
  <div id="app">
    <HeaderTitle :headerTitle="msg"/>
    <MemoList :memoList="memos" @add="addMemo" @delete="deleteMemo"/>
  </div>
</template>

<script>
import HeaderTitle from "./components/HeaderTitle.vue";
import MemoList from "./components/MemoList.vue";

export default {
  name: "App",
  components: {
    HeaderTitle,
    MemoList,
  },
  data () {
    return {
      msg: 'メモアプリ',
      text: '',
      editIndex: -1,
      memos: []
    }
  },
  mounted () {
    this.memos = JSON.parse(localStorage.getItem('memos')) || []
  },
  methods: {
    addMemo (text, index) {
      if (index === -1) {
        this.memos.push(text)
      } else {
        this.memos.splice(index, 1, text)
      }
      localStorage.setItem('memos', JSON.stringify(this.memos))
    },
    deleteMemo (index) {
      if (confirm('Are you sure?')) {
        this.memos.splice(index, 1)
      }
      this.text = ''
      localStorage.setItem('memos', JSON.stringify(this.memos))
    },
  }
}
</script>

<style>
</style>
