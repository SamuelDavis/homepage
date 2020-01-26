<template>
    <article>
        <label v-text="label"/>
        <p v-text="description"/>
    </article>
</template>

<script>
  export default {
    name: 'skill-description',
    props: {
      label: String,
      description: String
    }
  }
</script>

<style scoped>
    label {
        font-weight: bold;
    }
</style>
