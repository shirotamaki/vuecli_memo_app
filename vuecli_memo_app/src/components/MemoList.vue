<template>
  <div>
    <ul>
      <li v-for="(memo, index) in memoList" :key="index">
        <span @click="edit(index, memo)">{{ showTitle(memo) }}</span>
      </li>
    </ul>
  </div>
  <div>
    <form @submit.prevent>
      <textarea type="text" v-model="text" ref="editor"></textarea>
      <div>
        <span><button class="button" @click="setText" type="submit">{{ '＋' }}</button></span>
        <span><button class="button" @click="cancel" type="submit">キャンセル</button></span>
        <span><button class="button" @click="remove" type="submit">削除</button></span>
      </div>
    </form>
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
    edit (index, memo) {
      this.editIndex = index
      this.text = memo
      this.$refs.editor.focus()
    },
    setText () {
      this.$emit('add', this.text, this.editIndex)
      this.cancel()
    },
    cancel () {
      this.text = ''
      this.editIndex = -1
    },
    remove () {
      this.$emit('delete', this.editIndex)
    },
  },
}
</script>

<style>
</style>
