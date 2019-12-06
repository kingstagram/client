<template lang="html">
    <div class="ui form">
        <form class="ui form" @submit="login">
            <div class="ui grid">
                <div class="three wide column">
                    <label>Caption</label>
                    <input type="text" placeholder="Caption" size="50">
                </div>
                <div class="four wide column">
                    <label>Image</label>
                    <input type="file" placeholder="Image" accept=".gif,.jpg,.jpeg,.png">
                </div>
                <div class="four wide column">
                    <button class="ui black labeled icon button" @click.prevent="register">
                        <i class="user icon"></i>
                        Post it !
                    </button>
                </div>
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        name: "addPostingComponent"
    }
</script>

<style scoped>
    .form, .ui{
        border: none
    }
</style>