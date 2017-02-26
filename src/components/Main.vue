<template>
  <div class="container test_youtube_dl_front">
    
    <table class="table">
      <thead>
        <tr>
          <th>Img</th>
          <th>Title</th>
          <th>User</th>
          <th>youtubeId</th>
          
          <th>Duration</th>
          <th>View</th>
          <th>Description</th>
          <th>Created</th>
        </tr>
      </thead>
      
      <tbody>
      <tr v-for="d in videoData">
        <td><a v-bind:href="d.url"><img v-bind:src="d.thumbnail" class="img-thumbnail" /></a></td>
        <td>{{ d.fulltitle }}</td>
        <td>{{ d.userURL }}</td>
        <td>{{ d.youtube_id }}</td>
        
        <td>{{ d.duration }}</td>
        <td>{{ d.view_count }}</td>
        <td>{{ d.description }}</td>
        <td>{{ d.createdAt }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'test_youtube_dl_front',
  data() {
    return {
      videoData: {},
    };
  },
  created: function created() {
    // https://stackoverflow.com/questions/34215526/eslint-how-to-disable-unexpected-console-statement-in-node-js
    this.$http.get('http://test_youtube_dl_back.local/video')
    .then((res) => {
      /* eslint-disable no-console */
      this.videoData = res.data;
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
