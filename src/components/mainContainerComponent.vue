<template lang="html">
    <div class="ui container">
        <main-navbar-component></main-navbar-component>
        <div class="ui segment">
            <add-posting-component></add-posting-component>
        </div>
        <div class="ui four column grid">
            <div class="row">
                <card-component v-for="post in posts"
                                :key="post._id"
                                :post="post"
                                @like="getPosts"
                                @add-comment="getPosts"
                                class="column">
                </card-component>
            </div>
            <!--&lt;!&ndash;            <user-profile></user-profile>&ndash;&gt;-->
        </div>
    </div>
</template>

<script>
    import axios from 'axios';
    import mainNavbarComponent from "./mainNavbarComponent";
    import cardComponent from "./cardComponent";
    import addPostingComponent from "./addPostingComponent";
    // import userProfile from "./userProfile";
    const url = "http://104.198.195.12";

    export default {
        name: "mainContainerComponent",
        data() {
            return {
                posts: [],
                message: '',
                isMessage: false,
                author: null
            }
        },
        components: {
            mainNavbarComponent,
            cardComponent,
            addPostingComponent,
            // userProfile
        },
        methods: {
            getPosts: function () {
                axios({
                    method: 'get',
                    url: url + '/posts/all',
                    headers: {
                        token: localStorage.token
                    }
                }).then(response => {
                    console.log(response.data);
                    this.posts = response.data
                }).catch(err => {
                    this.message = err;
                    this.isMessage = true;
                });
            },
            getAuthor: function (userId) {
                axios({
                    method: 'get',
                    url: url + '/users/',
                    headers: {
                        token: localStorage.token
                    }
                }).then(response => {
                    console.log(response.data);
                    this.posts = response.data
                }).catch(err => {
                    this.message = err;
                    this.isMessage = true;
                });
            }
        },
        created() {
            this.getPosts()
        }
    }
</script>

<style scoped>
    .column{
        margin: 5px;
    }
</style>