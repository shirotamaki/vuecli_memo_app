<template>
  <form @submit.prevent class="container-form">
    <div class="form-button">
      <template v-if="isEditing">
        <textarea :value="editMemoText" @input="newText = $event.target.value" class="textarea"></textarea>
        <span><button class="button" @click="updateMemo" type="submit">編集</button></span>
        <span><button class="button" @click="deleteMemo" type="submit">削除</button></span>
      </template>
      <template v-else>
        <textarea @input="newText = $event.target.value" class="textarea"></textarea>
        <span><button class="button" @click="createMemo" type="submit">追加</button></span>
      </template>
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
    }
  },
  computed: {
    isEditing () {
      return this.editMemoIndex !== -1
    },
  },
  methods: {
    createMemo () {
      if (this.newText !== '') {
        this.$emit('create', this.newText)
      } else {
        this.cancel()
      }
    },
    updateMemo () {
      if (this.newText !== '') {
        this.$emit('update', this.newText, this.editMemoIndex)
      } else {
        this.cancel()
      }
    },
    deleteMemo () {
      this.$emit('delete', this.editMemoIndex)
    },
    cancel () {
      this.$emit('cancel')
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
