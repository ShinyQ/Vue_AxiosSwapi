<template>
  <div id="app">
    <h1>Star Wars Movie API</h1> 
        <table>
            <thead>
                <tr>
                <th>id</th>
                <th>Title</th>
                <th>Description</th>
                <th>Director</th>
                <th>Release Date</th>
                <th>Url</th>
                </tr>
            </thead>
            <GetApi :film="film" v-for="(film, index) in films"></GetApi>
          </table> 
  </div>
</template>

<script>
  import axios from 'axios'
  import GetApi from './components/GetApi.vue'
  export default {
    name: 'app',
    components: {    
      GetApi
    },
    data: function () {
      return {
        films: []
      }
    },
    methods: {
      fetchFilms: function () {
        axios.get('https://swapi.co/api/films/').then((response) => {
          this.films = response.data.results
          console.log(response.data.results)
        }, (error) => {
          console.log(error)
        })
      }
    },
    mounted: function () {
      this.fetchFilms()
    }
  }
</script>


<style>
  body {
    background-color: #444444;
    font-family: Verdana, Helvetica, Arial;
    font-size: 14px;
  }
  a img {
    border: none;
  }
  a {
    color: #0000FF;
  }
  .clear {
    clear: both;
    height: 0;
    overflow: hidden;
  }
  #app {
    width: 75%;
    margin: 0 auto;
    background-color: #FFF;
    padding: 20px 40px;
    border: solid 1px black;
    margin-top: 20px;
    position: relative;
  }
  #flash_notice, #flash_error, #flash_alert {
    padding: 5px 8px;
    margin: 10px 0;
    margin-right: 150px;
  }
  #flash_notice {
    background-color: #CFC;
    border: solid 1px #6C6;
  }
  #flash_error, #flash_alert {
    background-color: #FCC;
    border: solid 1px #C66;
  }
  .field_with_errors {
    display: inline;
  }
  .error_messages {
    width: 400px;
    border: 2px solid #CF0000;
    padding: 0px;
    padding-bottom: 12px;
    margin-bottom: 20px;
    background-color: #f0f0f0;
    font-size: 12px;
  }
  .error_messages h2 {
    text-align: left;
    font-weight: bold;
    padding: 5px 10px;
    font-size: 12px;
    margin: 0;
    background-color: #c00;
    color: #fff;
  }
  .error_messages p {
    margin: 8px 10px;
  }
  form .field, form .actions {
    margin: 12px 0;
  }
  h4 {
    margin-bottom: 5px;
  }
  table {
      border-collapse: collapse;
      width: 100%;
  }
  th, td {
      text-align: left;
      padding: 8px;
  }
  tr:nth-child(even){background-color: #f2f2f2}
  th {
      background-color: #4CAF50;
      color: white;
  }
</style>