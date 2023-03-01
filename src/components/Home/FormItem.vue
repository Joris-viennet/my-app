<template>
  <form class="form" @submit.prevent="onsubmit">
    <input type="text" placeholder="Title" v-model.trim.lazy="item.title" />
    <input type="text" placeholder="Content" v-model.trim.lazy="item.body" />
    <button class="btn btn-add" type="submit">Add</button>
  </form>
</template>

<script>
export default {
  emits: ['item-added'],
  data() {
    return {
      item: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    onsubmit() {
      if (this.item.title === '') {
        return
      }
      if (this.item.body === '') {
        return
      }

      this.$emit('item-added', this.item)
      this.item.title = ''
      this.item.body = ''
    }
  }
}
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

.btn-add {
  margin: 10px;
}
</style>
