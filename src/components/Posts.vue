<template>
  <div>
      <h3>{{msg}}</h3>
      <ul v-for="post in posts" :key="post">
          <li v-if="(post.id)%2 != 0">
             <ul> 
                 <li><strong>User ID:</strong> {{post.userId}}</li><br>
                 <li><strong>Post ID:</strong> {{post.id}}</li><br>
                 <li><strong>Title:</strong> {{post.title}}</li><br>
                 <li><strong>Post:</strong> {{post.body}}</li><br><hr><br>
             </ul>             
          </li>
      </ul>
      <button @click="fetchPosts">Fetch Posts</button>
  </div>
</template>

<script>
export default {
    name: "Posts",
    props: {
        msg: String
        },
    data(){
        return{
            userId: 0,
            id: 0,
            title: "",
            body: "",
            post: {},
            posts: [],
            baseURI: "https://jsonplaceholder.typicode.com/posts",
        };
    },
    methods:{
        fetchPosts: function(){
            this.$http.get(this.baseURI).then((result) => {
                this.posts = result.data;
            });
        },
    }
}
</script>

<style>

</style>