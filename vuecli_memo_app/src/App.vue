<template>
  <div id="app">
    <div class="container">
      <h1>メモアプリ</h1>
      <MemoList
          :memoList="memos"
          @edit="editMemo"
      />
      <MemoForm
          :editMemoIndex="editIndex"
          :editMemoText="text"
          @add="addMemo"
          @delete="deleteMemo"
      />
    </div>
  </div>
</template>

<script>
import MemoForm from './components/MemoForm.vue'
import MemoList from './components/MemoList.vue'

export default {
  name: 'App',
  components: {
    MemoList,
    MemoForm,
  },

  data () {
    return {
      editIndex: -1,
      text: '',
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
    editMemo (index, memo) {
      this.editIndex = index
      this.text = memo
    },
  },
}
</script>

<style scoped>
.container {
  width: 240px;
  border-width: 1px;
  border-style: solid;
  background-color: yellow;
  margin: 8px;
  padding: 12px;
}
</style>
