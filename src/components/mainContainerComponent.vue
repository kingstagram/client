<template lang="html">
    <div class="ui container">
        <main-navbar-component></main-navbar-component>
        <div class="ui segment">
            <p>
                <card-component></card-component>
            </p>
        </div>
    </div>
</template>

<script>
    import mainNavbarComponent from "./mainNavbarComponent";
    import cardComponent from "./cardComponent";

    export default {
        name: "mainContainerComponent",
        components: {
            mainNavbarComponent,
            cardComponent
        }
    }
</script>

<style scoped>

</style>