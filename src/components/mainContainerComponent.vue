<template lang="html">
    <div class="ui container">
        <main-navbar-component></main-navbar-component>
        <div class="ui segment">
            <add-posting-component></add-posting-component>
        </div>
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
    import addPostingComponent from "./addPostingComponent";

    export default {
        name: "mainContainerComponent",
        components: {
            mainNavbarComponent,
            cardComponent,
            addPostingComponent
        }
    }
</script>

<style scoped>

</style>