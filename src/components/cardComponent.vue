<template>
    <div class="ui card">
        <div class="content">
            <!-- tap to share button -->
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
            <!-- change to avatar -->
            <!-- <img class="ui avatar image" v-bind:src="post.useravatar"> -->
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
            <i class="heart outline like icon"></i>
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
                <input type="text" placeholder="Add Comment...">
                </form>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';
    // import commentModal from "./commentModal";

    export default {
        name: 'cardComponent',
        data () {
            return {
                showComment: false,
                comments: [],
                message: '',
                isMessage: false,
                username: localStorage.getItem('username')
            }
        },
        props: ['post'],
        methods: {
            viewComment: function(id) {
                axios({
                    method: 'get',
                    url: `http://localhost:3000/comments/all/${id}`,
                    headers: {
                        // token: localStorage.getItem('token')
                        token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZGU5ZDFkOTYyZjhkNzMzOGUxYzE5ZTIiLCJ1c2VybmFtZSI6ImFhYSIsImVtYWlsIjoiYmJiQG1haWwuY29tIiwiaWF0IjoxNTc1NjA0Njk3fQ.VG8s4hNlu6fg_zGD7qwGOeFCKre3ZZO15J-KFr0sGLM"
                    }
                }).then(response => {
                    console.log('masuk')
                    this.comments = response.data
                }).catch(err => {
                    this.message = err;
                    this.isMessage = true;
                });
                // this.$emit('readComment', id)
            },
            likePost: function() {

            }
        },
        components: {
            // messageComponent
        }
    }
</script>

<style scoped>

</style>

                