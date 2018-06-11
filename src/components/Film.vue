<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <template v-if="Object.keys(film).length">
          <div class="card">
            <img class="card-img" src="https://placehold.it/1068x400" alt="Card Image">
            <div class="card-img-overlay">
              <h1 class="card-title text-left">{{film[$route.params.id].title}}</h1>
              <p class="card-text text-left">{{film[$route.params.id].description}}</p>
            </div><br>
            <h3>В ролях:</h3>
            <div class="card-body">
              <div class="row">
                <div class="col-3" v-for="actor in film[$route.params.id].actors" :key="actor.id">
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
        </template>
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
