<template>
  <q-item clickable v-ripple class="bg-grey-3">
    <q-item-section side>
      {{ itemId + 1 }}
    </q-item-section>

    <q-item-section>
      {{ content }}
    </q-item-section>

    <q-item-section side>
      <q-btn
        icon="delete"
        size="sm"
        round
        @click="deleteItem"
      />
    </q-item-section>
  </q-item>
</template>

<script>
  export default {
    props: {
      content: {
        type: String
      },
      itemId: {
        type: Number
      }
    },

    methods: {
      deleteItem () {
        this.$emit('deleteItem', this.itemId)
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>
