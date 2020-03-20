<template>
  <q-card>
    <q-card-section>
      <ListAddTask @addTask="addTask" />

      <q-separator spaced />

      <draggable v-model="items" group="items">
        <ListItem
          v-for="(el, i) in items"
          :content="el"
          :key="`${el}-${i}`"
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

  data: () => ({
    items: [
    ]
  }),

  methods: {
    addTask (value) {
      this.items = [...this.items, value]
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
