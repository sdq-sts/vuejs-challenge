<template>
  <q-layout view="lHh Lpr lFf" class="q-pa-md">
    <div class="row">
      <div class="col-2">
        <List />
      </div>
    </div>
  </q-layout>
</template>

<script>
import List from '@/components/List'

export default {
  name: 'LayoutDefault',
  components: {
    List
  },
  data: () => ({

  })
}
</script>

<style>
</style>
