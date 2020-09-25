<template>
  <div>
      <h3>{{msg}}</h3>
      <ul>
          <li v-for="user in tasks" :key="user">
             <ul v-show="user.userId == 2 && user.completed != false"> 
                 <li><strong>USER ID:</strong> {{user.userId}}</li><br>
                 <li><strong>ID:</strong> {{user.id}}</li><br>
                 <li><strong>TITLE:</strong> {{user.title}}</li><br>
                 <li><strong>COMPLETED:</strong> {{user.completed}}</li><br><hr><br>
             </ul>             
          </li>
      </ul>
      <button @click="findById">RecoveryDataById</button>
  </div>
</template>

<script>
export default {
    name: "Todos",
    props: {
        msg: String
        },
    data(){
        return{
            userId: 0,
            id: 0,
            title: "",
            completed: "",
            user: {},
            tasks: [],
            baseURI: "https://jsonplaceholder.typicode.com/todos",
        };
    },
    methods:{
        findById: function(){
            this.$http.get(this.baseURI).then((result) => {
                this.tasks = result.data;
            });
        },
    }
}
</script>

<style>
    ul li ul li{
        text-align: left;
    }
</style>