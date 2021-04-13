<template>
  <div class="border flex flex-col md:flex-row mb-5 p-3 hover:shadow-md">
    <div class="md:w-1/2">
      <a
        :href="repo_html_url"
        target="_blank"
        class="text-blue-400"
      >
        {{repo_name}}
      </a>
      </div>
      <div class="md:w-1/2 mt-3 md:mt-0">
        <div class="badges flex space-x-5">
          <p class="bg-blue-400 rounded-md text-white px-3 py-1 text-xs">Stars: {{repo_stargazers_count}}</p>
          <p class="bg-gray-400 rounded-md text-white px-3 py-1 text-xs">Watchers: {{repo_watchers_count}}</p>
          <p class="bg-green-400 rounded-md text-white px-3 py-1 text-xs">Forks: {{repo_forks_count}}</p>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    'repo_html_url',
    'repo_name',
    'repo_stargazers_count',
    'repo_watchers_count',
    'repo_forks_count'
  ]  
}
</script>

<style scoped>

</style>