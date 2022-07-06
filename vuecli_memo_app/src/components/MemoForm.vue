<template>
    <form @submit.prevent>
      <span><button class="button" @click="addForm" type="submit">+</button></span>
      <div class="container-form" v-if="enable">
        <textarea v-model="text" class="textarea" type="text" required></textarea>
        <div class="form-button">
          <span><button class="button" @click="addMemo" type="submit">編集</button></span>
          <span><button class="button" @click="deleteMemo" type="submit">削除</button></span>
        </div>
      </div>
    </form>
</template>

<script>

export default {
  props: {
    editMemoIndex: Number,
    editText: String,
  },

  data () {
    return {
      text: '',
      editIndex: -1,
      memos: [],
      enable: false,
    }
  },

  methods: {
    addForm () {
      this.enable = true
    },
    addMemo () {
      this.$emit('add', this.text, this.editIndex)
      this.cancel()
    },
    cancel () {
      this.text = ''
      this.editIndex = -1
      this.enable = false
    },
    deleteMemo () {
      this.$emit('delete', this.editIndex)
      this.cancel()
    },
  },

  watch: {
    editMemoIndex: function(editMemoIndex) {
      this.editIndex = editMemoIndex
    },
    editText: function(editText) {
      this.text = editText
      this.enable = true
    }
  }
}
</script>

<style scoped>
.container-form {
  width: 200px;
  margin:0 auto;
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
