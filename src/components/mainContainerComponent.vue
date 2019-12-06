<template lang="html">
    <div class="ui container">
        <main-navbar-component></main-navbar-component>
        <div class="ui segment">
            <p>
                <card-component v-for="post in posts"
                                :key="post._id"
                                :post="post"
                ></card-component>
            </p>
            <user-profile></user-profile>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';
    import mainNavbarComponent from "./mainNavbarComponent";
    import cardComponent from "./cardComponent";
    import userProfile from "./userProfile";

    export default {
        name: "mainContainerComponent",
                data () {
            return {
                posts: [],
                message: '',
                isMessage: false,
            }
        },
        components: {
            mainNavbarComponent,
            cardComponent,
            userProfile
        },
        methods: {
            getPosts: function(){
                axios({
                    method: 'get',
                    url: 'http://localhost:3000/posts/all',
                    headers: {
                        // token: localStorage.getItem('token')
                        token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZGU5ZDFkOTYyZjhkNzMzOGUxYzE5ZTIiLCJ1c2VybmFtZSI6ImFhYSIsImVtYWlsIjoiYmJiQG1haWwuY29tIiwiaWF0IjoxNTc1NjA0Njk3fQ.VG8s4hNlu6fg_zGD7qwGOeFCKre3ZZO15J-KFr0sGLM"
                    }
                }).then(response => {
                    console.log(response.data)
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

</style>