<template>
  <q-item clickable v-ripple class="bg-grey-3">
    <q-item-section>
      {{ content }}
    </q-item-section>

    <q-item-section side>
      <span>2 min ago</span>
    </q-item-section>
  </q-item>
</template>

<script>
  export default {
    props: {
      content: {
        type: String
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>
