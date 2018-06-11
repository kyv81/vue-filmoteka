<template>
  <div class="card">
    <img src="https://via.placeholder.com/250x200" alt="" class="card-img-top">
    <div class="card-body">
      <h4 class="card-title">{{item.title}}</h4>
      <p class="card-text">{{item.description}}</p>
      <p>
        <span class="badge badge-light" v-for="tag in item.tags" :key="tag" @click="onTagClicked(tag)">#{{tag}}</span>
      </p>
      <div>
        <router-link class="btn btn-link" :to="`/films/${item.id}`">Подробнее</router-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FilmCard',
  props: ['item'],
  methods: {
    onTagClicked (tag) {
      this.$emit('tag', tag)
    }
  }
}
</script>

<style>
</style>
