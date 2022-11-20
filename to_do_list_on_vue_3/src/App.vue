<template>
  <header class="topHead">
    <my-button
        style="margin: auto"
        @click="showAboutSite"
    >О сайте
    </my-button>

    <my-button
        style="margin: auto"
        @click="showAboutMe"
    >Создатель
    </my-button>

    <my-button
        style="margin: auto"
        @click="showMore"
    >Посмотреть еще работы
    </my-button>
  </header>

  <div>
    <my-dialog v-model:show="AboutSite" style="text-align: center">
      <h1>Информация о сайте</h1>
      <p style="font-size: 20px">Этот сайт был написан в образовательных целях и
      <br>является показателем умения работать с Vue3.</p>
      <p><br>P.S. Сайт будет дорабатываться, по мере возможности.</p>
    </my-dialog>

    <my-dialog v-model:show="AboutMe" style="text-align: center">
      <h1>Гавран Иван</h1>
      <a href="https://www.linkedin.com/in/kisliyborsch/"
         style="font-size: 16px;text-decoration: none;color: #da18ff"
      >LinkedIn</a>
      <br>
      <a href="https://github.com/KisliY-Borsch"
         style="font-size: 16px;text-decoration: none;color: #da18ff"
      >GitHub</a>
      <br>
      <a href="https://www.instagram.com/kisliy_borsch/"
         style="font-size: 16px;text-decoration: none;color: #da18ff"
      >Instagram</a>
    </my-dialog>

    <my-dialog v-model:show="More" style="text-align: center">
      <h1><a href="https://github.com/KisliY-Borsch"
             style="text-decoration: none;color: #da18ff"
      >Мой GitHub</a></h1>
    </my-dialog>
  </div>

  <div class="app">
    <h1>Создание поста</h1>
    <my-button
        @click="showDialog"
        style="margin: 15px 0"
        >Добавить пост
    </my-button>
    <my-dialog v-model:show="dialogVisible">
      <post-form
          @create="createPost"
      />
    </my-dialog>
    <h1>Текущие посты</h1>
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
      AboutSite: false,
      AboutMe: false,
      More: false,
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
    showAboutSite(){
      this.AboutSite = true;
    },
    showAboutMe(){
      this.AboutMe = true;
    },
    showMore(){
      this.More = true;
    }
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
.topHead{
  display: flex;
  justify-content: space-around;
  background: darkslategrey;
}
</style>