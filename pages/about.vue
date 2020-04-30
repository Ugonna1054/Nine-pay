<template>
  <div>Hello About</div>
</template>

<script>
export default {
  asyncData() {
    return new Promise((resolve) => {
      // eslint-disable-next-line nuxt/no-timing-in-fetch-data
      setTimeout(function() {
        resolve({})
      }, 1000)
    })
  }
}
</script>

<style></style>
