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
          @create="createMemo"
          @update="updateMemo"
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
    createMemo (text) {
      this.memos.push(text)
      localStorage.setItem('memos', JSON.stringify(this.memos))
      this.text = ''
    },
    updateMemo (text, index) {
      this.memos.splice(index, 1, text)
      localStorage.setItem('memos', JSON.stringify(this.memos))
      this.text = ''
      this.editIndex = -1
    },
    deleteMemo (index) {
      this.memos.splice(index, 1)
      localStorage.setItem('memos', JSON.stringify(this.memos))
      this.text = ''
      this.editIndex = -1
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
