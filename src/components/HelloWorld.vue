<script setup lang="ts">
import axios from "axios";
import { ref, defineExpose } from "vue";

const posts = ref();
const open = ref(false);

const openModal = () => (open.value = true);

defineExpose({
  openModal,
});

await axios
  .get("https://jsonplaceholder.typicode.com/posts")
  .then((res) => (posts.value = res.data));
</script>

<template>
  <button @click="open = true">Open Modal</button>

  <Teleport to="body">
    <div class="modal" v-if="open === true">
      <div class="modal-content">
        <span class="close" @click="open = false">&times;</span>
        <p>Hello from modal !</p>
      </div>
    </div>
  </Teleport>

  <!-- <h1>Liste des Posts</h1>
  <ul>
    <li v-for="post in posts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </li>
  </ul> -->
  <div class="genant">CONTENU GENANT</div>
</template>

<style>
/* Style CSS pour la modale */
.modal {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.4);
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}

.genant {
  position: absolute;
  left: 0;
  top: 50;
  width: 10%;
  height: 10%;
  overflow: auto;
  background: lightblue;
  padding: 20px;
}
</style>
