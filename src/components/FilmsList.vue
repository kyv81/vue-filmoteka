<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <film-filter v-model="search" :tags="tags" @tag="onTagUnFilterClicked"></film-filter>
      </div>
    </div>
    <div class="row">
      <div class="col-3" v-for="film in filtered.slice(0, limit)" :key="film.id">
        <film-card :item="film" @tag="onTagFilterClicked"></film-card>
      </div>
    </div>
    <div class="row" v-if="limit < filtered.length">
      <div class="col text-center">
        <div class="btn btn-primary" @click="limit += 8">Загрузить еще</div>
      </div>
    </div>
    <div class="row" v-if="!filtered.length">
      <div class="col">
        <p class="text-center">По вашему запросу ничего не найдено</p>
      </div>
    </div>
  </div>
</template>

<script>
import FilmFilter from './FilmFilter'
import FilmCard from './FilmCard'
import axios from 'axios'

export default {
  name: 'FilmsList',
  data () {
    return {
      search: '',
      films: [],
      tags: [],
      limit: 8
    }
  },
  methods: {
    onTagFilterClicked (value) {
      if (!this.tags.includes(value)) {
        this.tags.push(value)
      }
    },
    onTagUnFilterClicked (value) {
      if (this.tags.includes(value)) {
        this.tags.splice(this.tags.indexOf(value), 1)
      }
    }
  },
  computed: {
    filtered () {
      let filter = this.search.toLowerCase().trim()
      let result = []

      if (filter === '') {
        result = this.films
      } else {
        result = this.films.filter(film => {
          if (!film.title.toLowerCase().indexOf(filter)) {
            return true
          }
        })
      }

      if (this.tags.length > 0) {
        return result.filter(item =>
          this.tags.every(tag => item.tags.includes(tag))
        )
      }

      return result
    }
  },
  components: { FilmFilter, FilmCard },
  created () {
    axios
      .get('/static/films.json')
      .then(response => {
        this.films = response.data
      })
      .catch(e => {
        console.log(e)
      })
  }
}
</script>

<style>
</style>
