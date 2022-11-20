<template>
  <div v-if="posts.length > 0">
    <div class="post" v-for="post in posts" :key="post.id"
    >
      <div>
        <div><strong>Название: </strong>{{post.title}}</div>
        <div><strong>Описание: </strong>{{post.body}}</div>
      </div>
      <div class="post_btns">
        <my-button @click="$emit('remove', post)">Удалить</my-button>
      </div>
    </div></div>
  <h1 v-else style="color: red">Список пуст!!!</h1>
</template>

<script>
import MyButton from "@/components/UI/MyButton.vue";
export default {
  components: {MyButton},
  props:{
    posts:{
      type: Array,
      required: true,
    }
  }
}
</script>

<style scoped>
.post{
  padding: 15px;
  border: 2px solid mediumaquamarine;
  margin-top: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>