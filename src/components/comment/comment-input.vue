<template>
  <div>
    <div class="input_title">
      <input class="input_name" v-model="name" placeholder="Enter a name">
      <textarea rows="10" cols="10" class="input_text" v-model="text" placeholder="Write a review" ></textarea>
      <div class="input_button_title">
        <button class="button_item" @click="addComments">POST</button>
      </div>
      <div class="input_show_created" v-show="complete">
        <div class="show_item">
          <span>
            Post created
          </span>
        </div>
      </div>
      <div class="input_show_noCreated" v-show="noComplete">
        <div class="show_item">
          <span>
            Enter a name and comment text
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'comment-input',
  data:() => ({
    name: '',
    text: '',
    complete: false,
    noComplete: false
  }),
  methods: {
    addComments() {
      if(this.name != '' && this.text != '') {
        this.$emit('add-comment', this.name, this.text)
        this.complete = true
        this.noComplete = false
        this.name = ''
        this.text = ''  
      } else {
        this.noComplete = true
        this.complete = false
        this.name = ''
        this.text = ''
      }
      
    }
  }
}  
</script>

<style>
.input_title {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  margin-bottom: 50px;
}

.input_name {
  width: 900px;
  height: 30px;
  margin-bottom: 10px;
  border-radius: 5px;
  border-color: #cccccc;
  background-color: #f2f2f2;
  border: 1px solid #cccccc;
  border-radius: 5px;
  font-size: 14px;
  padding: 0 15px;
}

.input_text {
  padding: 15px;
  width: 900px;
  height: 150px;
  margin-bottom: 10px;
  background-color: #f2f2f2;
  border-radius: 5px;
  border-color: #cccccc;
  font-size: 14px;
}

.input_button_title {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-end;
  width: 900px;
}

.button_item {
  padding: 8px 30px ;
  color: #ffffff;
  font-weight: 700;
  background-color: #2521ff;
  border: none;
  border-radius: 5px;
  transition: all .5s;
  cursor: pointer;
  display: inline-block;
}

.button_item:hover {
  background-color: #ffffff;
  border: 1px solid #2521ff;
  color: #2521ff;
}

.input_show_created {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  width: 900px;
  margin: 20px 0 0;
  border: 1px solid #05ff61;
  border-radius: 5px;
  background-color: #e8fff0;
  color: #00c763;
}

.input_show_noCreated {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  width: 900px;
  margin: 20px 0 0;
  border: 1px solid #ff3030;
  border-radius: 5px;
  background-color: #ffeded;
  color: #9e0000;
}

.show_item {
  padding: 10px;
}

@media screen and (max-device-width: 924px) {
  
  .input_name {
    width: 724px;
    height: 30px;
    margin-bottom: 10px;
    border-radius: 5px;
    border-color: #cccccc;
    background-color: #f2f2f2;
    border: 1px solid #cccccc;
    border-radius: 5px;
    font-size: 15px;
  }

  .input_text {
    padding: 15px;
    width: 724px;
    height: 150px;
    margin-bottom: 10px;
    background-color: #f2f2f2;
    border-radius: 5px;
    border-color: #cccccc;
    font-size: 14px;
  }

  .input_button_title {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-end;
    width: 724px;
  }

  .input_show_created {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    width: 724px;
    margin: 20px 0 0;
    border: 1px solid #05ff61;
    border-radius: 5px;
    background-color: #e8fff0;
    color: #00c763;
  }

  .input_show_noCreated {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    width: 724px;
    margin: 20px 0 0;
    border: 1px solid #ff3030;
    border-radius: 5px;
    background-color: #ffeded;
    color: #9e0000;
  }

}

@media screen and (max-device-width: 750px) {
  
  .input_name {
    width: 500px;
    height: 30px;
    margin-bottom: 10px;
    border-radius: 5px;
    border-color: #cccccc;
    background-color: #f2f2f2;
    border: 1px solid #cccccc;
    border-radius: 5px;
    font-size: 15px;
  }

  .input_text {
    padding: 15px;
    width: 500px;
    height: 150px;
    margin-bottom: 10px;
    background-color: #f2f2f2;
    border-radius: 5px;
    border-color: #cccccc;
    font-size: 14px;
  }

  .input_button_title {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-end;
    width: 500px;
  }

  .input_show_created {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    width: 500px;
    margin: 20px 0 0;
    border: 1px solid #05ff61;
    border-radius: 5px;
    background-color: #e8fff0;
    color: #00c763;
  }

  .input_show_noCreated {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    width: 500px;
    margin: 20px 0 0;
    border: 1px solid #ff3030;
    border-radius: 5px;
    background-color: #ffeded;
    color: #9e0000;
  }

}
</style>


