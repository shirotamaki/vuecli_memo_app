<template>
  <form @submit.prevent>
    <span><button class="button" @click="displayForm" type="submit">+</button></span>
    <div class="container-form" v-if="inputMode">
      <textarea class="textarea" type="text" v-model="text" ref="editor" required></textarea>
      <div class="form-button">
        <span><button class="button" @click="addMemo" type="submit">編集</button></span>
        <span><button class="button" @click="deleteMemo" type="submit">削除</button></span>
      </div>
    </div>
  </form>
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
    displayForm () {
      this.inputMode = true
    },
    editMemo (index, memo) {
      this.inputMode = true
      this.editIndex = index
      this.text = memo
      this.$refs.editor.focus()
    },
    addMemo () {
      this.$emit('add', this.text, this.editIndex)
      this.cancel()
    },
    cancel () {
      this.text = ''
      this.editIndex = -1
      this.inputMode = false
    },
    deleteMemo () {
      this.$emit('delete', this.editIndex)
      this.cancel()
    },
  },
}
</script>

<style>
.container-form {
  width: 200px;

}

.textarea {
  width: 200px;
  height: 200px;
}

.form-button {
  text-align: right;
}

.button {
  margin: 8px 0px 8px 8px;
}
</style>
