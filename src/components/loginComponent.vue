<template lang="html">
    <div class="page-login">
        <register-component v-if="isRegister" @backtohome="backtohome"></register-component>
        <div class="ui centered grid container" v-if="isLogin">
            <div class="nine wide column">
                <div class="ui icon warning message">
                    <i class="lock icon"></i>
                    <div class="content">
                        <div class="header">
                            Login failed!
                        </div>
                        <p>You might have misspelled your username or password!</p>
                    </div>
                </div>
                <div class="ui fluid card">
                    <div class="content">
                        <form class="ui form" @submit="login">
                            <div class="field">
                                <label>User Name</label>
                                <input type="text" name="username" placeholder="User Name">
                            </div>
                            <div class="field">
                                <label>Password</label>
                                <input type="password" name="password" placeholder="Password">
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

    export default {
        name: "loginComponent",
        data() {
            return {
                isRegister: false,
                isLogin: true
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
            login: function(e){
                e.prevent.default();
            }
        },
        components: {
            registerComponent
        }
    }
</script>

<style scoped>
    body {
        background-color: #ECF0F1;
    }

    .page-login {
        margin-top: 25px;
    }
</style>