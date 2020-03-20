<template>
  <q-card>
    <q-card-section>
      <div class="full-width row justify-between items-center">
        <span>TASK LIST {{ listId + 1 }}</span>
        <q-btn
          icon="delete"
          size="sm"
          round
          @click="removeList"
        />
      </div>
    </q-card-section>
    <q-separator spaced />

    <q-card-section>
      <ListAddTask @addTask="addTask" />

      <div v-if="items.length">
        <q-separator spaced />
          <p class="full-width row justify-between items-center q-ma-md">
            <q-btn
              icon="sort_by_alpha"
              size="sm"
              round
              @click="sortByAlpha"
            />
            <span class="text-bold">sort by alphabetical order</span>
          </p>
        <q-separator spaced />
      </div>

      <draggable group="items">
        <ListItem
          v-for="(el, i) in items"
          :itemId="i"
          :content="el"
          :key="`${el}-${i}`"
          @deleteItem="deleteItem"
          class="q-mb-md"
        />
      </draggable>

    </q-card-section>
  </q-card>
</template>

<script>
import draggable from 'vuedraggable'
import ListItem from '@/components/ListItem'
import ListAddTask from '@/components/ListAddTask'

export default {
  components: {
    draggable,
    ListItem,
    ListAddTask
  },

  props: {
    listId: {
      type: Number
    }
  },

  data: () => ({
    sortAlpha: false,
    items: []
  }),

  methods: {
    addTask (value) {
      this.items = [...this.items, value]
    },
    deleteItem (value) {
     this.items = this.items.filter((el, i) => i !== value)
    },
    removeList () {
      this.$emit('removeList', this.listId)
    },
    sortByAlpha() {
      this.sortAlpha = !this.sortAlpha

      this.sortAlpha
        ? this.items.sort((a, z) => a.localeCompare(z))
        : this.items.sort((a, z) => z.localeCompare(a))
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
