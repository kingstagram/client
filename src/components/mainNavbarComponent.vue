<template>
    <div>
        <div class="ui pointing menu">
            <a class="item active">
                Home
            </a>
            <a class="item">
                <i class="user link icon"></i>
                {{ username }}
            </a>
            <sui-popup basic content="The default theme's basic popup removes the pointing arrow.">
                <sui-button icon="add" slot="trigger" />
            </sui-popup>
            <a class="item" data-content="Add New Post">
                <i class="plus link icon"></i>
            </a>
            <div class="right menu">
                <div class="item">
                    <div class="ui transparent icon input">
                        <input type="text" placeholder="Search...">
                        <i class="search link icon"></i>
                    </div>
                </div>
            </div>
            <a class="item" @click="logout">
                Logout
            </a>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'mainNavbarcomponent',
        data() {
            return {
                username: localStorage.username
            };
        },
        methods: {
            logout: function () {
                localStorage.clear();
                location.reload();
            }
        },
    };
</script>