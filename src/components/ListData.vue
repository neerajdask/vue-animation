<template>
  <!-- <ul> -->
  <transition-group tag="ul" name="user-list">
    <li v-for="user in users" :key="user" @click="removeUser(user)">
      {{ user }}
    </li>
  </transition-group>
  <!-- </ul> -->

  <div>
    <input type="text" ref="inputUser" />
    <button @click="addUser()">Add user</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: ['Neeraj', 'Das', 'Suparna', 'Bbumani'],
    };
  },
  methods: {
    removeUser(user) {
      this.users = this.users.filter((usr) => usr !== user);
    },
    addUser() {
      const user = this.$refs.inputUser.value;
      this.users.unshift(user);
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 1rem 0;
  padding: 0;
}
li {
  border: 1px solid #ccc;
  padding: 1rem;
  text-align: center;
}

.user-list-enter-from {
  opacity: 0;
  transform: translateX(-30px);
}
.user-list-enter-active {
  transition: all 1s ease-out;
}
.user-list-enter-to {
  opacity: 1;
  transform: translateX(0px);
}

.user-list-leave-from {
  opacity: 1;
  transform: translateX(0px);
}
.user-list-leave-active {
  transition: all 1s ease-in;
  position: absolute;
}
.user-list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

.user-list-move {
  transition: transform 0.3s ease-out;
}
</style>