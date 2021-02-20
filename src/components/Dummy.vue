<template>
  <div>
    {{ id }}
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: Number,
      required: true
    }
  },
  updated () {
    console.log('Dummy updated')
  }
}
</script>