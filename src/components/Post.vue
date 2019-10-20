<template>
  <div class="post">
    <ul>
      <li v-for="post in posts" :key="post.id">{{ post.body }}</li>
    </ul>
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'

export default {
  name: 'Post',
  computed: {
    ...mapState(['posts'])
  },
  mounted () {
    this.$store.dispatch('getPosts')
  },
  methods: {
    ...mapActions (['getPosts'])
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
