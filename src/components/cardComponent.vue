<template>
  <div class="ui card">
    <div class="content">
      <div class="right floated meta">
        <div
          class="fb-share-button"
          :data-href="post.imageUrl"
          data-layout="button"
          data-size="small"
        >
          <a
            style="text-align: left"
            target="_blank"
            :href="
              'https://www.facebook.com/sharer/sharer.php?u=' + post.imageUrl
            "
            class="fb-xfbml-parse-ignore"
            onclick="javascript:window.open(this.href, '', 'menubar=no,toolbar=no,resizable=yes,scrollbars=yes,height=600,width=600');return false;"
          >
            <span style="text-align: left">
              <img
                src="https://www.pngkey.com/png/detail/207-2071361_facebook-share-icon-small.png"
                style="width: 60px"
              />
            </span>
          </a>
        </div>
      </div>
      <img class="ui avatar image" v-bind:src="post.userId.profileImage" />

      {{ username }}
    </div>
    <div class="image">
      <img v-bind:src="post.imageUrl" />
    </div>
    <div class="content">
      {{ post.caption }}
    </div>
    <div class="content">
      <span class="right floated">
        <i class="heart outline like icon" @click="likePost(post._id)"></i>
        {{ post.likes.length }}
      </span>
      <div>
        <i class="comment icon" @click="toggleModal"></i>
        {{ post.comments }}
      </div>
      <comment-modal :id="post._id" v-if="showModal"></comment-modal>
    </div>
    <!-- <div class="extra content"> -->
    <!-- <button type="button" class="btn btn-outline-primary btn-sm">View comment</button> -->
    <!-- <div class="ui large transparent left icon input">
                <form>
                    <i class="heart outline icon"></i>
                    <input @keyup.enter="addComment(post._id)" type="text" id="comment-input"
                           placeholder="Add Comment...">
                </form>
            </div> -->
    <!-- </div> -->
  </div>
</template>

<script>
import axios from "axios";

const url = "http://104.198.195.12";
import commentModal from "./commentModal";

export default {
  name: "cardComponent",
  data() {
    return {
      showModal: false,
      id: "",
      message: "",
      isMessage: false,
      username: null
    };
  },
  props: ["post"],
  methods: {
    likePost: function(id) {
      axios({
        method: "put",
        url: `${url}/posts/like/${id}`,
        headers: {
          token: localStorage.getItem("token")
        }
      })
        .then(response => {
          this.$emit("like");
        })
        .catch(err => {
          this.message = err;
          this.isMessage = true;
        });
    },

    toggleModal: function() {
      if (this.showModal) {
        this.showModal = false;
      } else {
        this.showModal = true;
      }
    }
  },
  components: {
    commentModal
  }
};
</script>

<style scoped>
.card {
  max-width: 19em;
  margin: 5px;
}
</style>
