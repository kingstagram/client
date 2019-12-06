<template>
    <div >
        <p>tes</p>
        <!-- <uploadForm></uploadForm>
        <cardComponent 
            v-for="post in posts"
            :key="post._id"
            :post="post"
        ></cardComponent> -->
    </div>
</template>

<script>
    import axios from 'axios';
    import cardComponent from "./cardComponent";
    import uploadForm from "./uploadForm";
    import userProfile from "./userProfile";
    import commentBox from "./commentBox";

    export default {
        name: "photoList",
        props: ['posts'],
        data: function() {
            return {
                posts: [
                        {"_id": "a",
                        "photoUrl": "https://www.arohatours.co.nz/media/1182/id29750pic5.jpg",
                        "username": "nana",
                        "times": "13h",
                        "likes": 10,
                        "comments": 10,
                        "caption": "ini foto nana",
                        "avatar": "https://www.arohatours.co.nz/media/1182/id29750pic5.jpg"                        
                        },
                        {"_id": "b",
                        "photoUrl": "https://www.tom-archer.com/wp-content/uploads/2017/03/landscape-photography-tom-archer-7.jpg",
                        "username": "lala",
                        "times": "1h",
                        "likes": 5,
                        "comments": 1,
                        "caption": "ini foto lala",
                        "avatar": "https://www.tom-archer.com/wp-content/uploads/2017/03/landscape-photography-tom-archer-7.jpg"                        
                        },
                        {"_id": "c",
                        "photoUrl": "https://static.photocdn.pt/images/articles/2017_1/iStock-545347988.jpg",
                        "username": "bubu",
                        "times": "3h",
                        "likes": 10,
                        "comments": 0,
                        "caption": "ini foto bubu",
                        "avatar": "https://static.photocdn.pt/images/articles/2017_1/iStock-545347988.jpg"                        
                        },
                        {"_id": "d",
                        "photoUrl": "https://cdn.pixabay.com/photo/2017/02/01/22/02/mountain-landscape-2031539__480.jpg",
                        "username": "sasa",
                        "times": "5h",
                        "likes": 2,
                        "comments": 10,
                        "caption": "ini foto sasa",
                        "avatar": "https://cdn.pixabay.com/photo/2017/02/01/22/02/mountain-landscape-2031539__480.jpg"                        
                        },
                        {"_id": "e",
                        "photoUrl": "https://cdn.pixabay.com/photo/2017/02/01/22/02/mountain-landscape-2031539__480.jpg",
                        "username": "kaka",
                        "times": "1h",
                        "likes": 1,
                        "comments": 3,
                        "caption": "ini foto kaka",
                        "avatar": "https://cdn.pixabay.com/photo/2017/02/01/22/02/mountain-landscape-2031539__480.jpg"                        
                        },
                        {"_id": "f",
                        "photoUrl": "https://image.shutterstock.com/image-photo/colorful-hot-air-balloons-flying-260nw-1033306540.jpg",
                        "username": "vivi",
                        "times": "2h",
                        "likes": 2,
                        "comments": 3,
                        "caption": "ini foto vivi",
                        "avatar": "https://image.shutterstock.com/image-photo/colorful-hot-air-balloons-flying-260nw-1033306540.jpg"                        
                        }
                    ]
            }
        },
        methods: {
            readComment: function(id) {
                this.showCommentBox(id)
            },
        },
        components: {
            cardComponent,
            uploadForm,
            userProfile,
            commentBox
        }
    };
</script>

<style scoped>
</style>