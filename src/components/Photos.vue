<template>
    <div>
      <h3>{{msg}}</h3>
      <ul v-for="album in albums" :key="album">
          <li v-if="album.albumId == 3">        
            <img :src="album.url" :alt="album.title">
            <ul>
                <li><strong>Album Id:</strong> {{album.albumId}}</li><br>
                <li><strong>Id:</strong> {{album.id}}</li><br>
                <li><strong>Title:</strong> {{album.title}}</li><br>
                <li><strong>URL:</strong> {{album.url}}</li><br>
                <li><strong>Thumbnail URL:</strong> {{album.thumbnailUrl}}</li><br><hr><br>
            </ul>    
          </li>
      </ul>
      <button @click="fetchAlbum">Fetch Album</button>

      <!-- 
            Album Id: {{album.albumId}}
            Id: {{album.id}}
            Title: {{album.title}}
            URL: {{album.url}}
            Thumbnail URL: {{album.thumbnailUrl}}

      -->
  </div>
</template>

<script>
export default {
    name: "Photos",
    props: {
        msg: String
        },
    data(){
        return{
            albumId: 0,
            id: 0,
            title: "",
            url: "",
            thumbnailUrl: "",
            album: {},
            albums: [],
            baseURI: "https://jsonplaceholder.typicode.com/photos/",
        };
    },
    methods:{
        fetchAlbum: function(){
            this.$http.get(this.baseURI).then((result) => {
                this.albums = result.data;
            });
        },
    }
}
</script>

<style>

</style>