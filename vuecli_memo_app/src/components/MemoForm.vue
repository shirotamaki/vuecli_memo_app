<template>
    <div>
      <form @submit.prevent>
        <textarea type="text" v-model="text" ref="editor"></textarea>
        <div>
          <span><button class="button" @click="setText" type="submit">{{ '＋' }}</button></span>
<!--          <span><button class="button" @click="cancel" type="submit">キャンセル</button></span>-->
<!--          <span><button class="button" @click="remove" type="submit">削除</button></span>-->
        </div>
      </form>
    </div>
</template>

<script>
export default {
  data () {
    return {
      text: '',
      editIndex: -1,
      memos: [],
    }
  },
  methods: {
    setText () {
        this.$emit("add", this.text)
        this.cancel()
    },
    cancel () {
      this.text = ''
      this.editIndex = -1
    },
  }
}

</script>

<style>
</style>
