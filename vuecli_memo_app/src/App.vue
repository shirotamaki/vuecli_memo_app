<template>
  <div id="app">
    <div class="container">
      <HeaderTitle :headerTitle="msg"/>
      <MemoList :memoList="memos" @edit="editMemoTrigger"/>
      <MemoForm @add="addMemo" @delete="deleteMemo" ref="MemoForm"/>
    </div>
  </div>
</template>

<script>
import HeaderTitle from './components/HeaderTitle.vue'
import MemoForm from './components/MemoForm.vue'
import MemoList from './components/MemoList.vue'

export default {
  name: 'App',
  components: {
    HeaderTitle,
    MemoList,
    MemoForm,
  },

  data () {
    return {
      msg: 'メモアプリ',
      text: '',
      editIndex: -1,
      memos: [],
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
      this.memos.splice(index, 1)
      this.text = ''
      localStorage.setItem('memos', JSON.stringify(this.memos))
    },
    editMemoTrigger (index, memo) {
      this.$refs.MemoForm.editMemo(index, memo)
    },
  },
}
</script>

<style>
.container {
  width: 240px;
  border-width: 1px;
  border-style: solid;
  background-color: yellow;
  margin: 8px;
  padding: 12px;
}
</style>
