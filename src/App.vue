<template>
    <div>
        <h1>{{ message }}</h1>
        <login-component/>

    </div>
</template>

<script>
    import loginComponent from "./components/loginComponent";

    export default {
        data: function () {
            return {
            };
        },
        components: {
            loginComponent
        }
    };
</script>

<style scoped>
</style>