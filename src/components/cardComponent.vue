<template>
    <div class="ui card">
        <div class="content">
            <!-- tap to share button -->
            <div class="right floated meta">14h</div>
            <!-- change to avatar -->
            <img class="ui avatar image" v-bind:src="post.useravatar">
            {{ username }}
        </div>
        <div class="image">
            <img v-bind:src="post.imageUrl">
        </div>
        <div class="content">
            {{post.caption}}
        </div>
        <div class="content">
            <span class="right floated">
                <i class="heart outline like icon" @click="likePost(post._id)"></i>
                {{post.likes.length}}
            </span>
            <div @click="viewComment(post._id)">
                <i class="comment icon"></i>
                <!-- {{post.comments}} -->
            </div>
        </div>
        <div class="extra content">
            <!-- <button type="button" class="btn btn-outline-primary btn-sm">View comment</button> -->
            <div class="ui large transparent left icon input">
                <form>
                    <i class="heart outline icon"></i>
                    <input @keyup.enter="addComment(post._id)" type="text" id="comment-input"
                           placeholder="Add Comment...">
                </form>
            </div>
        </div>
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
                showComment: false,
                comments: [],
                message: '',
                isMessage: false,
                username: null
            }
        },
        props: ['post'],
        methods: {
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
            addComment: function (id) {
                axios({
                    method: 'get',
                    url: `${url}//comments/add/${id}`,
                    headers: {
                        token: localStorage.getItem('token')
                        // token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZGU5ZDFkOTYyZjhkNzMzOGUxYzE5ZTIiLCJ1c2VybmFtZSI6ImFhYSIsImVtYWlsIjoiYmJiQG1haWwuY29tIiwiaWF0IjoxNTc1NjA0Njk3fQ.VG8s4hNlu6fg_zGD7qwGOeFCKre3ZZO15J-KFr0sGLM"
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

                