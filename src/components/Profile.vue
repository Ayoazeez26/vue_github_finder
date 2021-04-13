<template>
  <div class="mb-10">
    <div class="border rounded-md p-5 flex flex-col md:flex-row space-y-5 md:space-y-0 md:space-x-5">
      <div class="flex flex-col space-y-5 w-full md:w-1/4">
        <img class="rounded-lg" :src="user_avatar_url" alt="">
        <a :href="user_html_url" target="_blank" class="bg-blue-400 text-white p-3 rounded-2xl text-center hover:bg-blue-500 hover:shadow-md pointer">View Profile</a>
      </div>
      <div class="w-full md:w-3/4">
        <div class="badges flex flex-col md:flex-row md:space-x-3 space-y-3 md:space-y-0">
          <p class="bg-blue-400 rounded-md text-white px-3 py-1 text-xs">Public Repos: {{user_public_repos}}</p>
          <p class="bg-gray-400 rounded-md text-white px-3 py-1 text-xs">Public Gists: {{user_public_gists}}</p>
          <p class="bg-green-400 rounded-md text-white px-3 py-1 text-xs">Followers: {{user_followers}}</p>
          <p class="bg-indigo-400 rounded-md text-white px-3 py-1 text-xs">Following: {{user_following}}</p>
        </div>
        <div class="more-info border rounded-md mt-5 w-full">
          <div class="item border-b px-5 py-3">Company: {{user_company}}</div>
          <div class="item border-b px-5 py-3">Website/Blog: {{user_blog}}</div>
          <div class="item border-b px-5 py-3">Location: {{user_location}}</div>
          <div class="item border-b px-5 py-3">Member Since: {{user_created_at}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['user_avatar_url', 'user_html_url', 'user_public_repos', 'user_public_gists', 'user_followers', 'user_following', 'user_company', 'user_blog', 'user_location', 'user_created_at']  
}
</script>

<style scoped>

</style>