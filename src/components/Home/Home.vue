<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="title">
    <h1>Home</h1>
  </div>
  <FormItem @item-added="addItem" />
  <div class="content">
    <TransitionGroup name="bounce">
      <CardItem
        v-for="item in items"
        :title="item.title"
        :content="item.content"
        :key="item.id"
        @item-deleted="deleteItem(item.id)"
      />
    </TransitionGroup>
  </div>
</template>

<script>
import CardItem from './CardItem.vue'
import FormItem from './FormItem.vue'
import uniqueId from 'lodash.uniqueid'

export default {
  components: {
    CardItem,
    FormItem
  },
  data() {
    return {
      items: [
        { id: uniqueId('card-'), title: 'Bonjour', content: 'voila voila' },
        { id: uniqueId('card-'), title: 'Test', content: "C'est un autre test pour paragraphe" },
        { id: uniqueId('card-'), title: 'Status', content: 'voila voila' },
        { id: uniqueId('card-'), title: 'Toto', content: 'voila voila' }
      ]
    }
  },
  methods: {
    addItem(item) {
      this.items.push({ id: uniqueId('card-'), title: item.title, content: item.body })
    },
    deleteItem(idItem) {
      const itemIndex = this.items.findIndex((item) => item.id === idItem)
      this.items.splice(itemIndex, 1)
    }
  }
}
</script>

<style scoped>
.title {
  display: flex;
  justify-content: center;
}
.content {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}

.bounce-enter-active {
  animation: bounce-in 0.7s;
}
.bounce-leave-active {
  animation: bounce-in 0.7s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.2);
  }
  100% {
    transform: scale(1);
  }
}
</style>
