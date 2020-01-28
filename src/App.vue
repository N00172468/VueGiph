<template>
  <b-container>
    <b-row>
      <b-col>
        <GiphyViewer />
      </b-col>
    </b-row>
  </b-container>

</template>

<script>
import GiphyViewer from '@/components/GiphyViewer'

export default {
  name: 'app',
  components: {
    GiphyViewer,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
