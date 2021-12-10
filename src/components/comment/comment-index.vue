<template>
  <div class="comment_index" :name="theme">
    <div class="main">
      <div class="main_comment_title">
        <span>Comments</span>
      </div>
      <comment-input 
        @add-comment="addComment" 
      />
      <button 
      class="main_button_show" 
      @click.prevent="setPage"
      v-show="showButton"
      >
        {{button}}
      </button>
      <comment-list 
        :comment-list="responce" 
      />
    </div>
  </div>
</template>

<script>
import commentInput from './comment-input.vue'
import commentList from './comment-list.vue'



export default {
  name: 'index',
  components: {
    commentInput,
    commentList,

  },
  data:() => ({     
    responce: [],
    id: 0,
    button: 'Show More',
    pageNumber: 1,
    showButton: true,
    theme: 'light',
    totalPages: {},
    theme: ''
  }),
  created() {
    this.loadPost()
  },
  methods: {
    loadPost() {
      fetch('https://jordan.ashton.fashion/api/goods/30/comments?page=' + this.pageNumber++)
        .then(responce => {
          return responce.json()
        })
        .then(data => {
          this.responce = data.data
          this.totalPages = data
          console.log(this.responce)
        })
        .catch(error => {
          console.log(error)
      });
    },
    setPage() {
      if(this.pageNumber <= this.totalPages.last_page) {
        fetch('https://jordan.ashton.fashion/api/goods/30/comments?page=' + this.pageNumber++)
          .then(responce => {
            return responce.json()
          })
          .then(data => {
            this.responce = this.responce.concat(data.data)
            console.log(this.responce)
          })
          .catch(error => {
          console.log(error)
        });
        
      } else {
        return this.showButton = !this.showButton
      }
    },
    async addComment(name, text) {
      const res = await fetch('https://jordan.ashton.fashion/api/goods/30/comments', {
        method: 'POST',
        body: JSON.stringify({
          id: 0,
          name: name,
          text: text,
          visible: 0,
          product_id: 30,
          created_at: new Date(),
          updated_at: ''
        }),
        headers: {
          "Content-type": "application/json",
        }
      })
      console.log(res)
      this.loadPost()
    },
  }
}  
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nanum+Gothic:wght@400;700&family=Nunito:wght@300;400;500;600;700;800&family=Open+Sans+Condensed:wght@300;700&family=Roboto:wght@300&display=swap');

*{
  box-sizing: border-box;
  font-family: 'Nanum Gothic', sans-serif;
}

/*.comment_index[name="light"] {
  .main > .main_comment_title {
    background-color: #ffffff;
  }
}

.comment_index[name="dark"] {
  .main > .main_comment_title {
    background-color: #c7c7c7;
  }
} */

.main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.main_comment_title {
  display: flex;
  align-items: flex-start;
  width: 900px;
  margin-bottom: 10px;
  font-size: 19px;
  font-weight: 600;
}

.main_button_show {
  margin: 0 0 25px;
  text-transform: uppercase;
  font-weight: 600;
  padding: 8px 30px;
  border: none;
  border-radius: 5px;
  background-color: #2521ff;
  color: #ffffff;
  transition: all .5s;
  cursor: pointer;
}

.main_button_show:hover {
  background-color: #ffffff;
  border: 1px solid #2521ff;
  color: #2521ff;
}

.main_pagination {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 30px 0 0;
}

.pagination_page {
  padding: 8px;
  border: 1px solid #e7e7e7;
  margin: 0 5px;
}

@media screen and (max-device-width: 924px) {

  .main_comment_title {
    display: flex;
    align-items: flex-start;
    width: 724px;
    margin-bottom: 10px;
    font-size: 19px;
    font-weight: 600;
  }

}

@media screen and (max-device-width: 750px) {

  .main_comment_title {
    display: flex;
    align-items: flex-start;
    width: 500px;
    margin-bottom: 10px;
    font-size: 19px;
    font-weight: 600;
  }

}
</style>
