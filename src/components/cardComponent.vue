<template>
    <div class="ui card">
       <div class="content">
            <div class="right floated meta">14h</div>
            <img class="ui avatar image" v-bind:src="post.userId.profileImage">
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
                <input @keyup.enter="addComment(post._id)" type="text" id="comment-input" placeholder="Add Comment...">
                </form>
            </div> -->
        <!-- </div> -->

    </div>
</template>

<script>
    import axios from 'axios';
    import commentModal from "./commentModal";

    export default {
        name: 'cardComponent',
        data () {
            return {
                showModal: true,
                id: '',
                message: '',
                isMessage: false,
                username: localStorage.getItem('username')
            }
        },
        props: ['post'],
        methods: {
            likePost: function(id) {
                axios({
                    method: 'put',
                    url: `http://localhost:3000/posts/like/${id}`,
                    headers: {
                        // token: localStorage.getItem('token')
                        token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZGU5ZDFkOTYyZjhkNzMzOGUxYzE5ZTIiLCJ1c2VybmFtZSI6ImFhYSIsImVtYWlsIjoiYmJiQG1haWwuY29tIiwiaWF0IjoxNTc1NjA0Njk3fQ.VG8s4hNlu6fg_zGD7qwGOeFCKre3ZZO15J-KFr0sGLM"
                    }
                }).then(response => {
                    // console.log('masuk')
                    this.$emit('like')
                }).catch(err => {
                    this.message = err;
                    this.isMessage = true;
                });
            },
            toggleModal: function() {
                if (this.showModal) {
                    this.showModal = false
                } else {
                    this.showModal = true
                }
            }
        },
        components: {
            commentModal
        }
    }
</script>

<style scoped>

</style>

                