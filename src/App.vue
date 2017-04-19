<template>
  <div id="app">
    <img class="vue-logo" src="./assets/logo.png">
    <div class="vue-json-form">
      <h1>Vue JSON Form</h1>
      <json-form :label-width="80" v-model="myData"></json-form>
    </div>
  </div>
</template>

<script>
  import JsonForm from './components/JsonForm'

  export default {
    name: 'app',
    components: {
      JsonForm
    },
    data () {
      return {
        myData: {
          aString: 'this is a string',
          aNumber: 99,
          aNumberArray: [
            1, 2, 3
          ],
          aStringArray: [
            'a', 'b', 'c'
          ],
          anObject: {
            aStringInObj: 'this is a string in an Object',
            aNumberInObj: 0
          },
          aNull: null
        }
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 60px;
  }

  .vue-logo {
    display: block;
    margin: 0 auto;
  }

  .vue-json-form {
    display: block;
    margin: 0 auto;
    width: 60%;
  }
</style>
