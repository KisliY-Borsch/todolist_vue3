<template>

  <div class="app">
    <h1>Создание поста</h1>
    <my-button @click="showDialog">Добавить пост</my-button>
    <my-dialog v-model:show="dialogVisible">
      <post-form
          @create="createPost"
      />
    </my-dialog>
    <post-list
        :posts="posts"
        @remove = "removePost"
    />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyDialog from "@/components/UI/MyDialog.vue";
import MyButton from "@/components/UI/MyButton.vue";

export default {
  components:{
    MyButton,
    MyDialog,
    PostList, PostForm
  },
  data() {
    return {
      posts: [
        {id: 1, title: 'JavaScript', body: 'Курс о JavaScript Часть 1'},
        {id: 2, title: 'JavaScript 2', body: 'Курс о JavaScript Часть 2'},
        {id: 3, title: 'JavaScript 3', body: 'Курс о JavaScript Часть 3'},
      ],
      dialogVisible: false,
    }
  },
  methods:{
    createPost(post){
      this.posts.push(post);
    },
    removePost(post){
      this.posts = this.posts.filter(p => p.id !== post.id);
    },
    showDialog(){
      this.dialogVisible = true;
    },
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app{
  padding: 20px;
}
</style>