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
                isLogin: false,
            };
        },
        components: {
            loginComponent,
            mainContainerComponent
        }
    };
</script>

<style scoped>
</style>