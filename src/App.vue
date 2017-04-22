<template>
  <div id="app">
    <img class="vue-logo" src="./assets/logo.png">
    <div class="vue-json-form">
      <h1>Vue JSON Form</h1>
      <Input v-model="jsonString" type="textarea" :autosize="true" placeholder="JSON..."></Input>
      <br><br>
      <Button type="primary" @click="jsonToForm">Convert JSON to Form</Button>
      <br><br><br>
      <Button type="primary" @click="formToJSON">Convert Form to JSON</Button>
      <Button type="primary" @click="clear">Clear</Button>
      <br><br>
      <json-form ref="form" :label-width="80" v-model="myData"></json-form>
    </div>
    <Modal
        v-model="errorModal"
        title="Error">
      <p>
        {{error}}
      </p>
    </Modal>
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
        jsonString: '',
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
        },
        errorModal: false,
        error: ''
      }
    },
    methods: {
      jsonToForm () {
        try {
          this.myData = JSON.parse(this.jsonString)
        } catch (e) {
          this.error = 'Invalid JSON!'
          this.errorModal = true
        }
      },
      formToJSON () {
        try {
          this.jsonString = JSON.stringify(this.myData, null, 4)
        } catch (e) {
          this.error = 'Connot convert to JSON!'
          this.errorModal = true
        }
      },
      reset () {
        this.$refs['form'].reset()
      },
      clear () {
        this.$refs['form'].clear()
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
