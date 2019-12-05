<template>
    <div class="ui icon warning message">
        <i class="lock icon"></i>
        <div class="content">
            <div class="header">
                {{ title }}
            </div>
            <p>{{ message }}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: "message",
        props: {
            title: String,
            message: String
        },
        data() {
            return {
                title: this.props.title,
                message: this.props.message
            }
        }
    }
</script>

<style scoped>

</style>