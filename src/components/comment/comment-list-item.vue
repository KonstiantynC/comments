<template>
  <div>
    <div class="comments">
      <div class="comments_image">
        <img class="image" :src="image">
      </div>
      <div class="comment_item">
        <div class="comment_item_name">
          <span class="comment_name">{{ commentItem.name }}</span>
          <span>({{ time }})</span>   
        </div>
        <div class="comment_item_text">
          {{ commentItem.text}}  
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import image from '../../../assets/img/unknownPhoto.svg'
import moment from 'moment'

export default {
  name: 'comment-item',
  props: {
    commentItem: {
      type: Object,
      data: () => ({
      }),
      required:true
    }
  },
  data:() => ({
    image
  }),
  created() {
    this.time = moment(this.commentItem.created_at).startOf('second').fromNow() 
  },
}  
</script>


<style>
.comments {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-start;
  border-bottom: 1px solid #c2c2c2;
  width: 900px;
  padding: 0 0 10px;
}

.comment_item_name {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  flex-wrap: wrap;
  width: 820px;
}

.comment_item {
  display: flex;
  flex-direction: column;
  font-size: 16px;
}

.comment_item_text {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  flex-wrap: wrap;
  width: 820px;
  margin-top: 10px;
  flex-wrap: wrap;
}

.comments_image {
  margin-right: 40px;
}

.image {
  width: 40px;
  height: 40px;
}

.comment_name {
  font-size: 16px;
  font-weight: 600;
}

@media screen and (max-device-width: 924px) {
  .comments {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
    border-bottom: 1px solid #c2c2c2;
    width: 724px;
    padding: 0 0 10px;
  }

  .comment_item_text {
    box-sizing: border-box;
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    width: 644px;
    margin-top: 10px;
    flex-wrap: wrap;
  }

  .comment_item_name {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 644px;
  }

}

@media screen and (max-device-width: 750px) {
  .comments {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
    border-bottom: 1px solid #c2c2c2;
    width: 500px;
    padding: 0 0 10px;
  }

  .comment_item_text {
    box-sizing: border-box;
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    width: 420px;
    margin-top: 10px;
    flex-wrap: wrap;
  }

  .comment_item_name {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 420px;
  }

}
</style>