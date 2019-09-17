<template>
  <div id="app">
    <Header />
    <div id="content">
      <div class="user_card">
        <a v-for="user in users" :key="user._id.$oid" @click.prevent="showModal(user)"><UserCard :users="user"/></a>
      </div>
      <Pagination />
    </div>
    <Modal :user="content" :content="notes" v-show="isModalVisible" @close="closeModal"/>
  </div>
</template>

<script>
/* LIBS */
import axios from 'axios'

/* COMPONENTS */
import Header from "./components/Header";
import Modal from "./components/Modal"
import UserCard from "./components/User";
import Pagination from "./components/Pagination";

export default {
  name: "app",
  components: {
    Header,
    UserCard,
    Modal,
    Pagination

  },
  data(){
    return {
      users: [],
      isModalVisible: false,
      content: {},
      notes: {}
    }
  },
  methods: {
    getUsers() {
      axios
        .get("http://127.0.0.1:5000/api/v1/user/all")
        .then(res => {
          this.users = res.data;
          //this.totalRows = this.items.length;
        })
        .catch(err => console.log(err));
    }, 
    showModal(user) {
      this.content = user;
      this.getNotesUser(user._id.$oid);
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    },
    getNotesUser(user_id) {
      axios
        .get(`http://127.0.0.1:5000/api/v1/note/${user_id}`)
        .then(res => {
          this.notes = (res.data.length == 0) ? 'No contiene notas' : JSON.stringify(res.data, null, 4);
          //this.totalRows = this.items.length;
        })
        .catch(err => console.log(err));
    }
  },
  mounted(){
    this.getUsers()
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Nunito+Sans&display=swap");

html,
body {
  display: flex;
  flex-direction: column;
  height: 100%;
  margin: 0;
  padding: 0;
  font-family: "Nunito Sans", sans-serif;
}

#content {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
  height: calc(100% - 70px);
  align-self: center;
}

.user_card{
  width: 90%;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;

}

#app {
  text-align: center;
  background-color: #35495e;
  min-height: 100%;
}
</style>