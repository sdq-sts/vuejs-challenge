<template>
  <q-layout view="lHh Lpr lFf" class="q-pa-md">
    <draggable group="lists" class="row q-col-gutter-lg">
      <div class="col-3" v-for="(list, i) in lists" :key="list.id">
        <List
          :listId="i"
          @removeList="removeList"
        />
      </div>
    </draggable>

    <q-page-sticky position="bottom-right" :offset="[18, 18]">
      <q-btn
        color="primary"
        icon="add"
        size="lg"
        round
        @click="addList"
      />
    </q-page-sticky>
  </q-layout>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
import draggable from 'vuedraggable'
import List from '@/components/List'

export default {
  name: 'LayoutDefault',
  components: {
    List,
    draggable
  },
  data: () => ({
    lists: [
      { title: 'list-1', id: uuidv4() }
    ]
  }),
  methods: {
    addList () {
      this.lists = [
        ...this.lists, 
        { title: `list-${this.lists.length + 1}`, id: uuidv4() }
      ]
    },
    removeList (value) {
      this.lists = this.lists.filter((el, i) => i !== value)
      console.log(this.lists)
    }
  }
}
</script>

<style>
</style>
