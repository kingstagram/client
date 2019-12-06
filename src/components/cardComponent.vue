<template>
<!-- tap to share -->
    <div class="ui card">
        <div class="content">
            <!-- <div class="right floated meta">
                {{post.time}}
            </div> -->
            <img class="ui avatar image" :src="post.avatar"> {{post.username}}
        </div>
        <div class="image">
            <img :src="post.photoUrl">
        </div>
        <div class="content">
            {{post.caption}}
        </div>
        <div class="content">
            <span class="right floated">
            <i class="heart outline like icon"></i>
            {{post.likes}}
            </span>
            <i class="comment icon"></i>
            {{post.comments}}
        </div>
        <div class="extra content">
            <button type="button" class="btn btn-outline-primary btn-sm" @click="viewComment(post._id)">View/add comment</button>
            <div class="ui large transparent left icon input">
                <i class="heart outline icon"></i>
                <input type="text" placeholder="Add Comment...">
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        name: "cardComponent",
        data: function () {
            return {
                showComment: false
            }
        },
        methods: {
            viewComment: function(id) {
                this.$emit('readComment', id)
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

                