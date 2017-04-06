<template>
  <div>
    <Form class="json-form" :label-width="labelWidth">
      <json-node :prop="name" :value="data"></json-node>
    </Form>
  </div>
</template>

<script>
  import JsonNode from './JsonNode'

  export default {
    components: {
      JsonNode
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
      data: {
        type: Object
      }
    }
  }
</script>

<style scoped>

</style>
