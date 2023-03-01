<template>
  <div class="card">
    <button class="btn-delete top-right" @click="deleteItem">&#10005;</button>
    <span class="card_title">{{ title }}</span>
    <p class="card_content">
      {{ content }}
    </p>
  </div>
</template>

<script>
export default {
  emits: ['item-deleted'],
  props: {
    title: String,
    content: String
  },
  methods: {
    deleteItem() {
      this.$emit('item-deleted')
    }
  }
}
</script>

<style scoped>
.card {
  width: 200px;
  height: 210px;
  padding: 0 15px;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 12px;
  background: #e8e8e8;
  border-radius: 20px;
  margin: 10px;
  position: relative;
}

.card > * {
  margin: 0;
}

.card_title {
  font-size: 23px;
  font-weight: 900;
  color: #333;
}

.card_content {
  font-size: 13px;
  line-height: 18px;
  color: #333;
}

.top-right {
  position: absolute;
  top: 10px;
  right: 10px;
}
</style>
