<template>
  <div v-if="posts.length > 0">
  <transition-group name="p-list">

      <div class="post" v-for="post in posts" :key="post.id">
        <div>
          <div><strong>Название: </strong>{{post.title}}</div>
          <div><strong>Описание: </strong>{{post.body}}</div>
        </div>
        <div class="post_btns">
          <my-button @click="$emit('remove', post)">Удалить</my-button>
        </div>
      </div>
  </transition-group>
  </div>
  <h2 v-else style="color: red">Список пуст!!!</h2>
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
.p-list{
  display: inline-block;
  margin-right: 10px;
}
.p-list-enter-active,
.p-list-leave-active {
  transition: all 0.4s ease;
}
.p-list-enter-from,
.p-list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
</style>