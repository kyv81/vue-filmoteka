<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="card">
          <img class="card-img" src="https://placehold.it/1068x400" alt="Card Image">
          <div class="card-img-overlay">
            <h1 class="card-title text-left">{{actor.name}}</h1>
          </div>
          <h3>Фильмы:</h3>
          <div class="card-body">
            <div class="row">
              <div class="col-3" v-for="film in actor.films" :key="film.id">
                <router-link :to="`/films/${film.id}`" class="card">
                  <img class="card-img-top" src="https://placehold.it/150x100" alt="">
                  <div class="card-img-overlay">
                    <p class="card-title">{{film.title}}</p>
                  </div>
                </router-link>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Actor',
  data () {
    return {
      id: this.$route.params.id,
      actor: {}
    }
  },
  created () {
    axios.get('/static/actor.json').then(response => {
      this.actor = response.data
    })
  }
}
</script>

<style>
</style>
