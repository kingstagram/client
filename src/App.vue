<template>
    <div>
        <login-component v-if="!isLogin"></login-component>
        <main-container-component v-if="isLogin"></main-container-component>
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
            if (document.cookie){
                this.isLogin = true;
            } else {
                this.isLogin = false;
            }
        }
    };
</script>

<style scoped>
</style>