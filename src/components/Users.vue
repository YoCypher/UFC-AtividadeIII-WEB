<template>
  <div>
      <h3>{{msg}}</h3>
      <ul>
          <li v-for="user in users" :key="user">
              <ul v-if="user.id <= 5">
                  <li><strong>ID:</strong> {{user.id}}</li>
                  <li><strong>NAME:</strong>{{user.name}}</li>
                  <li><strong>EMAIL:</strong>{{user.email}}</li>
                  <li><strong>USERNAME:</strong>{{user.username}}</li>
                  <li><strong>ADDRESS:</strong> {{user.address.street}}, {{user.address.suite}}, {{user.address.city}} - {{user.address.zipcode}}</li>
                  <li><strong>GEOLOCALIZATION:</strong> LAT: {{user.address.geo.lat}} | LNG: {{user.address.geo.lng}}</li>
                  <li><strong>PHONE:</strong>{{user.phone}}</li>
                  <li><strong>WEBSITE:</strong> {{user.website}}</li>
                  <li><strong>COMPANY:</strong> {{user.company.name}} | "{{user.company.catchPhrase}}" | "{{user.company.bs}}" </li>
              </ul>
              <br><br>
          </li>
      </ul>
      <button @click="fetchUsers">Fetch Users</button>
  </div>
</template>

<script>
export default {
    name: "Users",
    props: {
        msg: String
    },
    data(){
        return{
            id: 0,
            name: "",
            email: "",
            username: "",
            address: {},
            phone: "",
            website: "",
            company: {},
            user: {},
            users: [],
            baseURI: "https://jsonplaceholder.typicode.com/users",
        };
    },
    methods: {
        fetchUsers: function(){
        this.$http.get(this.baseURI).then((result) => {
            this.users = result.data;
            });
        },
    },
}
</script>

<style>
     ul li { 
         list-style: none;
     }
     ul li ul li{
         text-align: left;
     }
</style>