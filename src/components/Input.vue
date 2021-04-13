<template>
  <div class="mt-10 w-11/12 mx-auto">
    <div class="input border rounded-md p-6 mb-10">
      <h1 class="text-3xl md:text-4xl font-bold">Search Github Users</h1>
      <p class="text-lg md:text-2xl text-gray-300">Enter a username to fetch a user profile and repos</p>
      <input
        type="text"
        class="user border focus:outline-none rounded-md p-3 mt-3 w-full"
        placeholder="Github Username..."
        v-model="repoName"
        v-on:keyup="checkUser"
      >
    </div>
    <profile
      :user_avatar_url="user_avatar_url"
      :user_html_url="user_html_url"
      :user_public_repos="user_public_repos"
      :user_public_gists="user_public_gists"
      :user_followers="user_followers"
      :user_following="user_following"
      :user_company="user_company"
      :user_blog="user_blog"
      :user_location="user_location"
      :user_created_at="user_created_at"
    />

    <div class="mb-10">
      <div class="show-repos">
        <h2 class="text-3xl mb-3 font-bold">Latest Repos</h2>
        <div
          v-for="repo in repos"
          :key="repo.id"  
        >
          <repo
            :repo_html_url="repo.html_url"
            :repo_name="repo.name"
            :repo_stargazers_count="repo.stargazers_count"
            :repo_watchers_count="repo.watchers_count"
            :repo_forks_count="repo.forks_count"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Profile from './Profile.vue'
  import Repo from "./Repo.vue";
// const Vue = require('vue');
const axios = require('axios');
export default {
  components: {
    'profile' : Profile,
    'repo' : Repo
  },
  name: 'Input',
  data() {
    return {
      repoName: '',
      user_avatar_url: '',
      user_html_url: '',
      user_public_repos: 0,
      user_public_gists: 0,
      user_followers: 0,
      user_following: 0,
      user_company: '',
      user_blog: '',
      user_location: '',
      user_created_at: '',
      repos: [],
    }
  },
  methods: {
    checkUser() {
      const client_id = '2b3af783db9be3a2c556';
      const client_secret = '117f4ae71f03a0f966e0e6fc4bb6e1bc3413405d';
      const repos_count = 5;
      const repos_sort = 'created: asc';

      axios
        .get(`https://api.github.com/users/${this.repoName}?client_id=${client_id}&client_secret=${client_secret}`)
        .then((res) => {
          console.log(res)
          this.showProfile(res.data)
        }).catch((err) => {
          console.log(err)
        });

      axios
        .get(`https://api.github.com/users/${this.repoName}/repos?per_page=${repos_count}&sort=${repos_sort}client_id=${client_id}&client_secret=${client_secret}`)
        .then((res) => {
          console.log(res)
          this.repos = [...res.data];
        }).catch((err) => {
          console.log(err)
        });
    },
    showProfile(user) {
      this.user_avatar_url = user.avatar_url;
      this.user_html_url = user.html_url;
      this.user_public_repos = user.public_repos;
      this.user_public_gists = user.public_gists;
      this.user_followers = user.followers;
      this.user_following = user.following;
      this.user_company = user.company;
      this.user_blog = user.blog;
      this.user_location = user.location;
      this.user_created_at = user.created_at;
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
