<template>
    <div>
        <!-- <h1>KINGSTAGRAM</h1> -->
        <login-component v-if="!isLogin"></login-component>
        <main-container-component class="animated fadeInDown" v-if="isLogin"></main-container-component>
    </div>
</template>

<script>
    import loginComponent from "./components/loginComponent";
    import mainContainerComponent from "./components/mainContainerComponent";

    export default {
        data: function () {
            return {
                cookies: document.cookie,
                isLogin: false
            };
        },
        components: {
            loginComponent,
            mainContainerComponent
        },
        mounted(){
            if (localStorage.token && localStorage.username){
                this.isLogin = true;
            } else {
                this.isLogin = false;
            }
        }
    };
</script>

<style scoped>
    login-component {
        font-family: 'Raleway', sans-serif;
    }
</style>
