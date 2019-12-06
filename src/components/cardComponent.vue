<template>
    <div class="ui card">
<<<<<<< HEAD
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
                                :href="'https://www.facebook.com/sharer/sharer.php?u=' + post.imageUrl"
                                class="fb-xfbml-parse-ignore"
                                onclick="javascript:window.open(this.href, '', 'menubar=no,toolbar=no,resizable=yes,scrollbars=yes,height=600,width=600');return false;"
                            >
                                <span style="text-align: left">
                                <img src="https://www.pngkey.com/png/detail/207-2071361_facebook-share-icon-small.png" style="width: 60px">
                                </span>
                            </a>
                        </div>
            </div>
            <img class="ui avatar image" v-bind:src="post.userId.profileImage">
=======
        <div class="content">
            <!-- tap to share button -->
            <div class="right floated meta">14h</div>
            <!-- change to avatar -->
            <img class="ui avatar image" v-bind:src="post.useravatar">
>>>>>>> 1875e9dd88208751894755026c646de450dd30c2
            {{ username }}
        </div>
        <div class="image">
            <img v-bind:src="post.imageUrl">
        </div>
        <div class="content">
            {{ post.caption }}
        </div>
        <div class="content">
            <span class="right floated">
                <i class="heart outline like icon" @click="likePost(post._id)"></i>
                {{post.likes.length}}
            </span>
            <div>
                <i class="comment icon" @click="toggleModal"></i>
                 {{post.comments}}
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
    import axios from 'axios';

    const url = "http://104.198.195.12";
    // import commentModal from "./commentModal";

    export default {
        name: 'cardComponent',
        data() {
            return {
                showModal: false,
                id: '',
                message: '',
                isMessage: false,
                username: null
            }
        },
        props: ['post'],
        methods: {
<<<<<<< HEAD
            likePost: function(id) {
=======
            viewComment: function (id) {
                axios({
                    method: 'get',
                    url: `${url}/comments/all/${id}`,
                    headers: {
                        token: localStorage.token
                    }
                }).then(response => {
                    console.log('masuk')
                    this.comments = response.data
                }).catch(err => {
                    this.message = err;
                    this.isMessage = true;
                });
            },
            likePost: function (id) {
>>>>>>> 1875e9dd88208751894755026c646de450dd30c2
                axios({
                    method: 'put',
                    url: `${url}//posts/like/${id}`,
                    headers: {
                        token: localStorage.getItem('token')
                    }
                }).then(response => {
                    this.$emit('like')
                }).catch(err => {
                    this.message = err;
                    this.isMessage = true;
                });
            },
<<<<<<< HEAD
            toggleModal: function() {
                if (this.showModal) {
                    this.showModal = false
                } else {
                    this.showModal = true
                }
=======
            addComment: function (id) {
                axios({
                    method: 'get',
                    url: `${url}//comments/add/${id}`,
                    headers: {
                        token: localStorage.getItem('token')
                    },
                    data: {
                        content: document.getElementById('comment-input')
                    }
                }).then(response => {
                    console.log('masuk')
                    this.$emit('add-comment')
                }).catch(err => {
                    this.message = err;
                    this.isMessage = true;
                });
>>>>>>> 1875e9dd88208751894755026c646de450dd30c2
            }
        },
        components: {
            // commentModal
        }
    }
</script>

<style scoped>
    .card {
        max-width: 19em;
        margin: 5px;
    }
</style>

                