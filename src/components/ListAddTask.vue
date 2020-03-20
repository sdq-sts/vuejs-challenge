<template>
  <div class="row q-col-gutter-x-md">
    <div class="col-8">
      <q-input
        v-model="text"
        label="Add a new task"
        outlined
        dense
      />
    </div>
    <div class="col-4">
      <q-btn
        color="primary"
        size="md"
        label="Go!"
        class="full-width full-height"
        @click="addTask"
      />
    </div>
  </div>
</template>

<script>
  export default {
    data: () => ({
      text: '',
    }),
    methods: {
      addTask() {
        if (this.text) {
          this.$emit('addTask', this.text)
        }
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>
