<template>
  <div>
    <form class="ui reply form" @submit.prevent="addComment">
      <div class="field">
        <input type="text" v-model="content" />
      </div>
    </form>
    <div class="ui comments">
      <div class="comment">
        <div class="content" v-for="comment in comments" :key="comment._id">
          <!-- <a class="author">{{ comment.userId.username }}</a> -->
          <div class="metadata">
            <span class="date"> {{ comment.content }} </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "commentModal",
  data: function() {
    return {
      comments: [],
      content: ""
    };
  },
  props: ["id"],
  methods: {
    getComments: function() {
      axios({
        method: "get",
        url: `http://104.198.195.12/comments/all/${this.id}`,
        headers: {
          token: localStorage.getItem("token")
          //token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZGU5ZDFkOTYyZjhkNzMzOGUxYzE5ZTIiLCJ1c2VybmFtZSI6ImFhYSIsImVtYWlsIjoiYmJiQG1haWwuY29tIiwiaWF0IjoxNTc1NjA0Njk3fQ.VG8s4hNlu6fg_zGD7qwGOeFCKre3ZZO15J-KFr0sGLM"
        }
      })
        .then(response => {
          console.log("comments masuk");
          this.comments = response.data;
        })
        .catch(err => {
          this.message = err;
          this.isMessage = true;
        });
      // this.$emit('comments')
    },
    addComment: function() {
      // alert("masuk comment");
      // console.log(this.id);
      axios({
        method: "post",
        url: `http://104.198.195.12/comments/add/${this.id}`,
        headers: {
          token: localStorage.getItem("token")
          // token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZGU5ZDFkOTYyZjhkNzMzOGUxYzE5ZTIiLCJ1c2VybmFtZSI6ImFhYSIsImVtYWlsIjoiYmJiQG1haWwuY29tIiwiaWF0IjoxNTc1NjA0Njk3fQ.VG8s4hNlu6fg_zGD7qwGOeFCKre3ZZO15J-KFr0sGLM"
        },
        data: {
          content: this.content
        }
      })
        .then(response => {
          // console.log("masuk");
          this.getComments();
          this.content = "";
        })
        .catch(err => {
          this.message = err;
          this.isMessage = true;
        });
    },
    getId(id) {
      this.id = id;
    }
  },
  components: {},
  created() {
    this.getComments();
  }
};
</script>

<style></style>
