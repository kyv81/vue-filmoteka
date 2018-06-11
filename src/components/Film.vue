<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="card">
          <img class="card-img" src="https://placehold.it/1068x400" alt="Card Image">
          <div class="card-img-overlay">
            <h1 class="card-title text-left">{{film.title}}</h1>
            <p class="card-text text-left">{{film.description}}</p>
          </div><br>
          <h3>В ролях:</h3>
          <div class="card-body">
            <div class="row">
              <div class="col-3" v-for="actor in film.actors" :key="actor.id">
                <router-link :to="`/actors/${actor.id}/${actor.name}`" class="card">
                  <img class="card-img-top" src="https://placehold.it/150x100" alt="">
                  <div class="card-img-overlay">
                    <p class="card-title">{{actor.name}}</p>
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
  name: 'Film',
  data () {
    return {
      id: this.$route.params.id,
      film: {}
    }
  },
  created () {
    axios.get('/static/film.json').then(response => {
      this.film = response.data
    })
  }
}
</script>

<style>
</style>
