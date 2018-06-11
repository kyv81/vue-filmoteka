<template>
  <form>
    <div class="form-group">
      <input type="text" id="filter" class="form-control" :value="value" @input="onValueUpdated($event.target.value)">
    </div>
    <p>
      <span class="badge badge-light" v-for="tag in tags" :key="tag" @click="onTagClicked(tag)">#{{tag}}</span>
    </p>
  </form>
</template>

<script>
export default {
  name: 'FilmFilter',
  props: ['value', 'tags'],
  methods: {
    onValueUpdated (value) {
      this.$emit('input', value)
    },
    onTagClicked (tag) {
      this.$emit('tag', tag)
    }
  }
}
</script>

<style>
</style>
