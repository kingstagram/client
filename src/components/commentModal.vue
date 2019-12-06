<template>
  <div class="ui basic modal">
    <div class="content">
      <div class="ui comments">
  <h3 class="ui dividing header">Comments</h3>
  
  <div class="comment" v-for="comment in comments"
                                :key="comment._id"
                                :comments="comments">
    <a class="avatar">
      <!-- <img src="/images/avatar/small/matt.jpg"> -->
    </a>
    <div class="content">
      <a class="author"> {{ comment.userId }} </a>
      <!-- <div class="metadata">
        <span class="date">Today at 5:42PM</span>
      </div> -->
      <div class="text">
        {{ comment.content }}
      </div>
    </div>

  </div>
  </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'commentModal',
    data: function() {
            return {
                comments: []
            };
        },
    props: ['comments'],
    methods: {
        viewModal: function() {
          // this.$emit('comments')
        }
    },
    components: {
        
    },
    created() {
        // this.viewModal()
    }
}
</script>

<style>

</style>