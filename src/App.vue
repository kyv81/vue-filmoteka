<template>
  <div id="app">
    <app-title :title="title"></app-title>
    <div class="container">
      <div class="row">
        <div class="col">
          <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
              <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
              <div class="navbar-nav">
                <router-link to="/" class="nav-item nav-link">Фильмы</router-link>
                <router-link to="/actors" class="nav-item nav-link">Актеры</router-link>
              </div>
            </div>
          </nav>
        </div>
      </div>
    </div>
    <router-view/>
  </div>
</template>

<script>
import AppTitle from './components/AppTitle'

export default {
  name: 'App',
  data () {
    return {
      title: 'Фильмотека'
    }
  },
  components: { AppTitle }
}
</script>

<style lang="scss" src="./styles/styles.scss">
</style>
