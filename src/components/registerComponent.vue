<template lang="html">
    <div class="ui centered grid container" >

        <div class="nine wide column" id="border">
<!--            message here-->
            <message-component v-if="isMessage" :title="title" :message="message"></message-component>

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
    import messageComponent from "./messageComponent";

    export default {
        name: "registerComponent",
        data: function () {
            return {
                username:null,
                password:null,
                email:null,
                isMessage: false,
                message: null,
                title: "User Regitration"
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
                    url: 'http://104.198.195.12/users/register',
                    data: {
                        username: this.username,
                        password: this.password,
                        email:this.email
                    }
                }).then(response => {
                    this.message = "User successfully created";
                    this.isMessage = true;
                    localStorage.token = response.data.token;
                    localStorage.username = response.data.username;
                    location.reload();
                }).catch(err => {
                    this.message = err;
                    this.isMessage = true;
                });
            }
        },
        components: {
            messageComponent
        }
    }
</script>

<style scoped>
    #registerwrapper {
        padding-top: 10px;
        /* padding-bottom:  */
    }
    #border {
        width: 50%;
        border: 1px solid lightgray;
        border-radius: 1rem;
        padding: 25px;

    }

</style>