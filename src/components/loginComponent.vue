<template lang="html">
    <div class="page-login" id="login">
        <!--        register component here-->
        <register-component v-if="isRegister" @backtohome="backtohome"></register-component>
        <div class="ui centered grid container" v-if="isLogin">
            <div class="nine wide column animated pulse">
                <!--                message component here-->
                <message-component v-if="isMessage" :title="title" :message="message"></message-component>
                <div class="ui fluid card">
                    <div class="content">
                        <form class="ui form" @submit="login">
                            <div class="field">
                                <label>Email</label>
                                <input type="text" name="email" placeholder="Email" v-model="email">
                            </div>
                            <div class="field">
                                <label>Password</label>
                                <input type="password" name="password" placeholder="Password" v-model="password">
                            </div>
                            <button class="ui primary labeled icon button" type="submit">
                                <i class="unlock alternate icon"></i>
                                Sign In
                            </button>
                            <button class="ui black labeled icon button" @click.prevent="register">
                                <i class="user icon"></i>
                                Sign Up
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import registerComponent from "./registerComponent";
    import messageComponent from "./messageComponent";
    import axios from 'axios';

    export default {
        name: "loginComponent",
        data() {
            return {
                isRegister: false,
                isLogin: true,
                isMessage: false,
                email: null,
                password: null,
                message: null,
                title: "User Sign In"
            }
        },
        methods: {
            register: function () {
                this.isRegister = true,
                    this.isLogin = false
            },
            backtohome: function () {
                this.isRegister = false,
                    this.isLogin = true
            },
            login: function (e) {
                e.preventDefault()
                axios({
                    method: 'post',
                    url: 'http://104.198.195.12/users/login',
                    data: {
                        email: this.email,
                        password: this.password
                    }
                }).then(response => {
                    this.message="User successfully login";
                    this.isMessage = true;
                    localStorage.token = response.data.token;
                    localStorage.username = response.data.username;
                    location.reload();
                }).catch(err => {
                    this.message = err;
                    this.isMessage = true;
                })
            }
        },
        components: {
            registerComponent,
            messageComponent
        }
    }
</script>

<style scoped>
    #login {
        padding-top: 13rem;
    }
    body {
        background-color: #ECF0F1;
    }

    .page-login {
        margin-top: 25px;
    }
</style>