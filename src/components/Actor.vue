<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <template v-if="Object.keys(actor).length">
          <div class="card">
            <img class="card-img" src="https://placehold.it/1068x400" alt="Card Image">
            <div class="card-img-overlay">
              <h1 class="card-title text-left">{{$route.params.name}}</h1>
            </div><br>
            <h3>Фильмы:</h3>
              <div class="card-body">
                <div class="row">
                  <div class="col-3" v-for="film in actor[$route.params.id].films" :key="film.id">
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
        </template>
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
