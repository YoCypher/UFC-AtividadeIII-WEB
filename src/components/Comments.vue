<template>
  <div>
      <h3>{{msg}}</h3>
      <ul v-for="comment in comments" :key="comment">
          <li v-if="(comment.id)%2 == 0">
             <ul> 
                 <li><strong>Post ID:</strong> {{comment.postId}}</li><br>
                 <li><strong>Comment ID:</strong> {{comment.id}}</li><br>
                 <li><strong>Name:</strong> {{comment.name}}</li><br>
                 <li><strong>Email:</strong> {{comment.email}}</li><br>
                 <li><strong>Comment:</strong> {{comment.body}}</li><br><hr><br>
             </ul>
          </li>
      </ul>
      <button @click="fetchComments">Fetch Comments</button>
  </div>
</template>

<script>
export default {
    name: "Comments",
    props: {
        msg: String
        },
    data(){
        return{
            postId: 0,
            id: 0,
            name: "",
            email: "",
            body: "",
            comment: {},
            comments: [],
            baseURI: "https://jsonplaceholder.typicode.com/comments",
        };
    },
    methods:{
        fetchComments: function(){
            this.$http.get(this.baseURI).then((result) => {
                this.comments = result.data;
            });
        },
    }
}
</script>

<style>
    ul li{
        text-align: left;
    }
</style>