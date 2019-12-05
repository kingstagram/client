<template>
    <div>
        <div class="ui pointing menu">
            <a class="item active">
                Home
            </a>
            <a class="item">
                Messages
            </a>
            <a class="item">
                Friends
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
        <div class="ui segment">
            <p></p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'mainNavbarcomponent',
        data() {
            return {};
        },
        methods: {
            logout: function () {
                document.cookie = "";
                location.reload();
            }
        },
    };
</script>