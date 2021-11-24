<template>
  <div>
    <div class="user" v-if="loading === false">
      <avatar circle size="sm" :img="userData.avatar_url"/>
      <user :profile="profileUser"/>
      <div class="repositories">
        <ul id="myList" v-if="userRepositories.length > 0">
        <h4>Repositories</h4>
        <small>Total Repositories: {{userRepositories.length}}</small>

          <li v-for="repository in userRepositories" :key="repository.id">{{repository.name}}</li>
        </ul>
      </div>
    </div>
    <div v-if="loading" style="margin-top: 40px; align-items: center; justify-content: center;">
      <cube-spin v-if="loading"/>
    </div>
  </div>
</template>

<script>
import Avatar from "./Avatar.vue"
import User from "./User";
import CubeSpin from 'vue-loading-spinner/src/components/RotateSquare2'
export default {
  components: { Avatar, User, CubeSpin },
  name: "",
  props: {
    userName: String
  },
  data: () => ({
    userData: "",
    userRepositories: [],
    loading: false,
  }),
  computed: {
    profileUser () {
      return {
        name: this.userData.name,
        bio: this.userData.bio,
        location: this.userData.location,
        blog: this.userData.blog
      };
    }
  },
  methods: {
    getUser(name) {
      this.loading = true
      fetch(`https://api.github.com/users/${name}`, {
        headers: {
          Accept: "application/json",
          "Content-Type": "application/json"
        },
        method: "GET"
      })
        .then(response => {
          response.json().then(x => (this.userData = x))
          this.loading = false
        })
        .catch(error => { 
          console.log(error)
          this.loading = false
        });
    },
    getRepos(name) {
      fetch(`https://api.github.com/users/${name}/repos`, {
        headers: {
          Accept: "application/json",
          "Content-Type": "application/json"
        },
        method: "GET"
      })
        .then(response => response.json().then(x => (this.userRepositories = x)))
        .catch(error => console.log(error));
    },
  },

  watch: {
    userName(context) {
      this.getUser(context);
      this.getRepos(context);
    }
  }
};
</script>

<style>
  .repositories {
    border: 1px solid gray;
    display: flex;
    /* padding: 20px; */
    width: 100%;
    color: #0969da;
    font-family: 'Shippori Antique', sans-serif;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background: #fff;
    
    margin-top: 20px;
    border-radius: 9px;
  }

  .repositories h4 {
    text-align: center;
    font-size: 20px;
    
  }

  .user {
    max-width: 100%;
    margin-top: 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
    flex-wrap: wrap;
    background-size: cover;
    background-position: center center;
    /* box-shadow: 30px 30px 30px -5px rgba(0, 0, 0, 0.3);
    transition: box-shadow 0.5s; */
    /* will-change: transform; */
    margin-bottom: 40px;
    padding: 20px;
  }

  /* .user:hover {
    box-shadow: 30px 30px 30px 35px rgba(0, 0, 0, 0.3);
  } */

  ul > h4 {
    margin-bottom: 2px;
    /* display: flex;
    flex-direction: row; */
  }
  li {
    border: 1px solid gray;
    border-radius: 9px;
    padding: 20px;
    margin-right: 17px;
    margin-top: 10px;
    display: flex;
    flex-direction: columns;
    /* text-decoration: none;
    list-style: none; */
  }
  small {
    font-weight: 600;
    font-size: 14px;
  }
</style>
