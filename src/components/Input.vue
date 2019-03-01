<template>
  <form @submit.prevent="addTodo">
    <input type="text" v-model="text">
    <button type="submit">Add</button>
  </form>
</template>

<script>
export default {
  name: 'Input',
  data () {
    return {
      text: ''
    }
  },
  methods: {
    addTodo () {
      if (this.text.trim() === '') return
      this.$emit('addTodo', this.text)
      this.text = ''
    }
  }
}
</script>
