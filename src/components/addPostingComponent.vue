<template lang="html">
    <div class="ui form">
        <form class="ui form" @submit="postIt">
            <div class="ui menu">
                <div class="item">
                    <input type="text" placeholder="Caption" size="50" v-model="caption">
                </div>
                <div class="item">
                    <label>Image</label>
                    <input id="file" type="file" placeholder="Image" accept=".gif,.jpg,.jpeg,.png">
                </div>
                <div class="item">
                    <button class="ui black labeled icon button" type="submit">
                        <i class="user icon"></i>
                        Post it !
                    </button>
                </div>
            </div>
        </form>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        name: "addPostingComponent",
        data() {
            return {
                caption: null
            }
        },
        methods: {
            postIt: function (e) {
                e.preventDefault();

                let formData = new FormData();
                let imagefile = document.querySelector('#file');
                formData.append("image", imagefile.files[0]);
                axios.post('http://104.198.195.12/posts/add',
                    {
                        caption: this.caption,
                        imageUrl: formData},
                    {
                    headers: {
                        'Content-Type': 'multipart/form-data'
                    }
                }).then(response => {
                    console.log(response)
                }).catch(err => {
                    console.log(err);
                })
            },
            file: function(){

            }
        }
    }
</script>

<style scoped>
    .form, .ui {
        border: none
    }
</style>