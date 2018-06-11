<template>
  <div class="container">
    <div class="card-body">
      <div class="row">
        <div class="col-3" v-for="actor in actors" :key="actor.id">
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

<script>
import axios from 'axios'

export default {
  name: 'ActorsList',
  data () {
    return {
      actors: []
    }
  },
  created () {
    axios.get('/static/actors.json').then(response => {
      this.actors = response.data
    })
  }
}
</script>

<style>
</style>
