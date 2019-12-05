<template lang="html">
    <div class="ui container">
        <main-navbar-component></main-navbar-component>
        <p></p>
    </div>
</template>

<script>
    import mainNavbarComponent from "./mainNavbarComponent";

    export default {
        name: "mainContainerComponent",
        components: {
            mainNavbarComponent
        }
    }
</script>

<style scoped>

</style>