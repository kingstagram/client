<template lang="html">
    <div class="ui centered grid container">

        <div class="nine wide column">
            <div class="ui icon warning message" v-if="isMessage">
                <i class="lock icon"></i>
                <div class="content">
                    <div class="header">
                        Registration User
                    </div>
                    <p>{{ message }}</p>
                </div>
            </div>

            <form class="ui form" @submit="registerUser">
                <div class="field">
                    <label>User Name</label>
                    <input type="text" name="username" placeholder="User Name" v-model="username">
                </div>
                <div class="field">
                    <label>Email</label>
                    <input type="email" name="email" placeholder="Email" v-model="email">
                </div>
                <div class="field">
                    <label>Password</label>
                    <input type="password" name="password" placeholder="Password" v-model="password">
                </div>
                <button class="ui primary labeled icon button" type="submit">
                    <i class="user alternate icon"></i>
                    Register
                </button>
                <button class="ui red labeled icon button" @click.prevent="backToHome">
                    <i class="home alternate icon"></i>
                    Home
                </button>
            </form>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        name: "registerComponent",
        data: function () {
            return {
                username:null,
                password:null,
                email:null,
                isMessage: false,
                message: null
            }
        },
        methods: {
            backToHome: function(){
                this.$emit('backtohome','')
            },
            registerUser: function(e){
                e.preventDefault();
                axios({
                    method: 'post',
                    url: 'http://localhost:3000/users/register',
                    data: {
                        username: this.username,
                        password: this.password,
                        email:this.email
                    }
                }).then(response => {
                    this.message = "User successfully created";
                    this.isMessage = true;
                }).catch(err => {
                    this.message = err;
                    this.isMessage = true;
                });
            }
        }
    }
</script>

<style scoped>

</style>