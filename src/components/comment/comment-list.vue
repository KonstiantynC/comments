<template>
  <div>
    <div class="list_title">
      <span>{{ commentList.length }} Responses</span>
    </div>
    <div class="list_container">
      <ul 
      v-for="(item, index) in paginationComment"
      :key="`item-${index}`"
      class="list_item" 
      >
        <li>
          <comment-item
          :comment-item="item"
          />  
        </li>
      </ul>  
    </div>
    <div class="main_pagination">
      <div 
        class="pagination_page"
        v-for="page in pages"
        :key="page"
        :class="{'page_selected': page === pageNumber}"
        @click="swapPage(page)"
      >
        {{ page }}
      </div>
    </div>
  </div>
</template>

<script>
import commentItem from './comment-list-item.vue'

export default {
  name: 'comment-list',
  components: {
    commentItem
  },
  props: {
    commentList: {
      type: Object,
      data: () => ({
      }),
      required:true
    }
  },
  data:() => ({
    itemsPerPage: 10,
    pageNumber: 1
  }),
  computed: {
    pages() {
      return Math.ceil(this.commentList.length / 10)
    },
    paginationComment() {
      let from = (this.pageNumber - 1) * this.itemsPerPage
      let to = from + this.itemsPerPage
      return  this.commentList.slice(from, to)
    }
  },
  methods: {
    swapPage(page) {
      this.pageNumber = page
    }
  }
}  
</script>

<style>
.list_container {
  box-sizing: border-box;
  /*border-bottom: 1px solid #c2c2c2;*/
  border-top: 3px solid #c2c2c2;
  width: 900px;
}

.list_item {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  list-style-type: none;
  padding-left: 0;
  margin: 20px 0 0 ;
}

.list_title {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  font-size: 18px;
  font-weight: 600;
  padding: 0 0 10px;
}

.pagination_page {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 30px;
  height: 35px;
  color: #2521ff;
  font-weight: 600;
  background-color: #ffffff;
  border: none;
  border-radius: 5px;
  transition: all .5s;
  cursor: pointer;
}

.pagination_page:hover {
  background-color: #2521ff;
  border: none;
  color: #ffffff;
}

.page_selected {
  background-color: #2521ff;
  border: none;
  color: #ffffff;
}

@media screen and (max-device-width: 924px) {
  .list_container {
    box-sizing: border-box;
    /*border-bottom: 1px solid #c2c2c2;*/
    border-top: 3px solid #c2c2c2;
    width: 724px;
  }

}

@media screen and (max-device-width: 750px) {
  .list_container {
    box-sizing: border-box;
    /*border-bottom: 1px solid #c2c2c2;*/
    border-top: 3px solid #c2c2c2;
    width: 500px;
  }

}

</style>
