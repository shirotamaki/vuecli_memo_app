<template>
  <div id="app">
    <div class="container">
      <h1>メモアプリ</h1>
      <MemoList
          :memoList="memos"
          @edit="editMemo"
      />
      <CreateMemoButtonForm
          @open="openForm"
      />
      <template v-if="isDisplaying">
        <MemoForm
            :editMemoIndex="editIndex"
            :editMemoText="text"
            @create="createMemo"
            @update="updateMemo"
            @delete="deleteMemo"
            @cancel="cancelMemo"
        />
      </template>
    </div>
  </div>
</template>

<script>
import MemoForm from './components/MemoForm.vue'
import MemoList from './components/MemoList.vue'
import CreateMemoButtonForm from './components/CreateMemoButtonForm.vue'

export default {
  name: 'App',
  components: {
    MemoList,
    MemoForm,
    CreateMemoButtonForm,
  },
  data () {
    return {
      editIndex: -1,
      text: '',
      memos: [],
      isFormEnabled: false,
    }
  },
  mounted () {
    this.memos = JSON.parse(localStorage.getItem('memos')) || []
  },
  computed: {
    isDisplaying () {
      return this.isFormEnabled
    }
  },
  methods: {
    createMemo (text) {
      this.memos.push(text)
      localStorage.setItem('memos', JSON.stringify(this.memos))
      this.isFormEnabled = false
    },
    updateMemo (text, index) {
      this.memos.splice(index, 1, text)
      localStorage.setItem('memos', JSON.stringify(this.memos))
      this.text = ''
      this.editIndex = -1
      this.isFormEnabled = false
    },
    deleteMemo (index) {
      this.memos.splice(index, 1)
      localStorage.setItem('memos', JSON.stringify(this.memos))
      this.text = ''
      this.editIndex = -1
      this.isFormEnabled = false
    },
    editMemo (index, memo) {
      this.editIndex = index
      this.text = memo
      this.isFormEnabled = true
    },
    cancelMemo() {
      this.isFormEnabled = false
    },
    openForm() {
      this.isFormEnabled = true
    }
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
