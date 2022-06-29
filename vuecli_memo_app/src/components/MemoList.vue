<template>
  <div>
    <ul>
      <li v-for="(memo, index) in memoList" :key="index">
        <span @click="edit(index, memo)">{{ displayTitle(memo) }}</span>
      </li>
    </ul>
  </div>

  <form @submit.prevent>
    <span><button class="button" @click="displayForm" type="submit">+</button></span>

    <div class="container-form" v-if="inputMode">
      <textarea class="textarea" type="text" v-model="text" ref="editor" required></textarea>
    </div>

    <div class="form_button">
      <span><button class="button" @click="addMemo" type="submit">編集</button></span>
      <span><button class="button" @click="deleteMemo" type="submit">削除</button></span>
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
    displayForm() {
      this.inputMode = true
    },
    edit (index, memo) {
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

.form_button {
  /*text-align: center;*/
}

.button {
  margin: 8px;
}
</style>
