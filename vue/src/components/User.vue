<template>
  <div type="button" class="card" id="users._id.$oid">
    <img class="avatar" src="../assets/avatar.png" alt />
    <h1>{{users.name}} {{users.last_name}}</h1>
    <hr />
    <h3>{{users.email}}</h3>
    <h3>{{users.gender}}</h3>
    <h3>{{users.age}}</h3>
  </div>
</template>

<script>

/* COMPONENT */

export default {
  name: "UserCard",
  props: {
    users: Object
  },
  methods: {
    check(item) {
      console.log(item);
    },
    select: function(event) {
      console.log(event.target)
    }
  }
};
</script>

<style scoped>
.card {
  background-color: #48bc85;
  min-width: 260px;
  margin: 20px;
  border-radius: 5px;
  box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.56);
  padding: 10px 3px 10px 3px;
  cursor: pointer;
  transition: 0.1s;
  color: #fff;
}

.card:hover {
  box-shadow: 0px 0px 35px rgba(0, 0, 0, 0.7);
  transform: scale(1.05,1.05);
}

.avatar {
  height: 100px;
  width: auto;
  border-radius: 50%;
}

hr {
  width: 80%;
  border-color: #fff;
}

h3 {
  margin: 5px;
}
</style>