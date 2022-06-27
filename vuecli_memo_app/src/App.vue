<template>
  <div id="app">
    <HeaderTitle :headerTitle="msg"/>
    <MemoList :memoList="memos"/>
    <MemoForm @add="addMemo"/>
  </div>
</template>

<script>
import HeaderTitle from "./components/HeaderTitle.vue";
import MemoList from "./components/MemoList.vue";
import MemoForm from "./components/MemoForm.vue";
// import EditDelete from "./components/EditDelete.vue";

export default {
  name: "App",
  components: {
    HeaderTitle,
    MemoList,
    MemoForm,
  },
  data() {
    return {
      msg: 'メモアプリ',
      text: '',
      editIndex: -1,
      memos: []
    }
  },
  methods: {
    addMemo(text) {
      this.memos.push(text)
    }
  },
  // mounted () {
  //   this.memos = JSON.parse(localStorage.getItem('memos')) || []
  // },
}
</script>

<style>
</style>
