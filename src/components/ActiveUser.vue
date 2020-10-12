<template>
  <p>Active User Component</p>
  <h2>{{ username }}</h2>
  <h3>{{ age }}</h3>
</template>

<script>
// this is called the 'config object'
export default {
  props: [ 'username', 'age' ]
}
</script>