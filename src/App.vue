<template>
    <div>
        <!-- <p>tes</p> -->
        <!-- <h1>{{ message }}</h1> -->
        <photo-list></photo-list>
        <!-- <login-component></login-component> -->
    </div>
</template>

<script>
    import loginComponent from "./components/loginComponent";
    import photoList from "./components/photoList";

    export default {
        data: function () {
            return {
            }
        },
        components: {
            loginComponent,
            photoList,
        }
    };
</script>

<style scoped>
</style>
