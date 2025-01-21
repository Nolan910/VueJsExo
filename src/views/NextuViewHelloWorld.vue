<script lang="ts">
import { ref } from 'vue'

export default {
  name: 'NextuViewHelloWorld',
  props:{
    count: {
        type: number,
        default: 2,
    },
  },
  setup(props) {
    const message = ref('Hi queen')
    const countData = props.count
    return {
      message,
      countData,
    }
  },
}

</script>
<template>
  <div>{{ message }} {{ countData }}</div>
</template>
<style></style>
