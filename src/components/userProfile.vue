<template>
  <div class="ui card">
    <!-- <div class="image">
    <img v-bind:src="user.avatar">
  </div> -->
    <div class="content">
      <a class="header"> {{ user.username }} </a>
      <div class="email">
        {{ user.email }}
      </div>
    </div>
    <!-- <div class="extra content"> -->
    <!-- <a>
      <i class="user icon"></i>
      22 Friends
    </a> -->
    <!-- </div> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "userProfile",
  data: function() {
    return {
      user: "",
      message: "",
      isMessage: false
    };
  },
  components: {
    // messageComponent
  },
  methods: {
    getUser: function() {
      axios({
        method: "get",
        url: "http://104.198.195.12/users/user",
        headers: {
          token: localStorage.getItem("token")
          // token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZGU5ZDFkOTYyZjhkNzMzOGUxYzE5ZTIiLCJ1c2VybmFtZSI6ImFhYSIsImVtYWlsIjoiYmJiQG1haWwuY29tIiwiaWF0IjoxNTc1NjA0Njk3fQ.VG8s4hNlu6fg_zGD7qwGOeFCKre3ZZO15J-KFr0sGLM"
        }
      })
        .then(user => {
          console.log(user.data);
          this.user = user.data;
        })
        .catch(err => {
          this.message = err;
          this.isMessage = true;
        });
    }
  },
  created() {
    this.getUser();
  }
};
</script>

<style></style>
