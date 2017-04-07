<template>
  <div>
    <Form class="json-form" :label-width="labelWidth">
      <json-node v-model="value" :prop="name"></json-node>
    </Form>
  </div>
</template>

<script>
  import JsonNode from './JsonNode'
  import { Form } from 'iview'

  export default {
    components: {
      'json-node': JsonNode,
      'Form': Form
    },
    props: {
      labelWidth: {
        type: Number,
        default: 40
      },
      name: {
        type: String,
        default: ''
      },
      value: {}
    }
  }
</script>

<style scoped>

</style>
