<template>
  <div id="app">
    <tablazat :rows="rows" @post-row-changed="Changed" @post-new="New" @post-row-delete="Delete"/>
    
  </div>
</template>

<script>
import Tablazat from './components/Tablazat.vue'


export default {
  name: 'App',
  components: {
    Tablazat
  },
  data() {
    return {
      rows: [
        {
          nev: 'Tekken',
          kiadasi_ev: 1998,
          kiado: 'Tekken Zrt',
          free_to_play:'Igen'
        },
        {
          nev: 'World of Warcraft',
          kiadasi_ev: 2003,
          kiado: 'Blizzard',
          free_to_play:'Nem'

        },
        {
          nev: 'League of Legends',
          kiadasi_ev: 2010,
          kiado: 'Riot Games',
          free_to_play:'Igen'

        },
        {
          nev: 'Heroes IV',
          kiadasi_ev: 2003,
          kiado: 'Heroes XD',
          free_to_play:'Igen'

        },
      ]
    }
  },
  methods: {
      Changed(e) {
        this.rows.map(function (row) {
          if (row.nev != e.original.nev || row.kiadasi_ev != e.original.kiadasi_ev || row.kiado != e.original.kiado || row.free_to_play !=e.original.free_to_play) {
            return row
          }
          row.nev = e.new.nev,
          row.kiadasi_ev = e.new.kiadasi_ev,
          row.kiado = e.new.kiado,
          row.free_to_play=e.new.free_to_play
          return row
        })
      },
      New(e){
        this.rows.push(e.new)
      },
      Delete(e){
          this.rows.splice(this.rows.indexOf(e.original), 1);
        }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
table{
  margin-left: auto;
  margin-right: auto;
}
</style>
