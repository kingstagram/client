<template>
    <div class="ui pointing menu">
        <a class="active item">Home</a>
        <a class="item">Messages</a>
        <a class="item">Friends</a>
        <div class="right menu">
            <div class="item">
                <div class="ui transparent icon input">
                    <input type="text" placeholder="Search...">
                    <i class="search link icon"></i>
                </div>
            </div>
        </div>
        <a class="ui item">Logout</a>
    </div>
</template>

<script>
    export default {
        name: "mainNavbarComponent"
    }
</script>

<style scoped>

</style>