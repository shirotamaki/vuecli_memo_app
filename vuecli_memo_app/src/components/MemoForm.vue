<template>
  <form @submit.prevent>
    <span><button class="button" @click="addForm" type="submit">+</button></span>
    <div class="container-form" v-if="isFormEnabled">
        <textarea :value="editMemoText" @input="newText = $event.target.value" class="textarea" required>
        </textarea>
      <div class="form-button">
        <span v-if="isEditing"><button class="button" @click="updateMemo" type="submit">編集</button></span>
        <span v-else><button class="button" @click="createMemo" type="submit">追加</button></span>
        <span><button class="button" @click="deleteMemo" type="submit">削除</button></span>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  props: {
    editMemoIndex: Number,
    editMemoText: String,
  },
  data () {
    return {
      newText: '',
      isFormEnabled: false,
    }
  },
  computed: {
    isEditing () {
      return this.editMemoIndex !== -1
    },
  },
  methods: {
    addForm () {
      this.isFormEnabled = true
    },
    createMemo () {
      this.$emit('create', this.newText)
      this.cancel()
    },
    updateMemo () {
      this.$emit('update', this.newText, this.editMemoIndex)
      this.cancel()
    },
    cancel () {
      this.isFormEnabled = false
    },
    deleteMemo () {
      this.$emit('delete', this.editMemoIndex)
      this.cancel()
    },
    inputEditText (value) {
      this.newText = value
      console.log(this.newText)
    },
  },
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
