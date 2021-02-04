<script>
  import { onMount } from "svelte";
  import User from "./components/User.svelte";
  import UserSearch from "./components/UserSearch.svelte";
  let users;

  onMount(() => {
    githubUsers();
  });

  const githubUsers = () => {
    fetch("https://api.github.com/users")
      .then(res => res.json())
      .then(data => {
        users = data;
      });
  };
</script>

<main>
  <UserSearch />

  {#if users}
    <ul>
      {#each users as user}
        <li>
          <User username={user.login} avatar={user.avatar_url} />
        </li>
      {/each}
    </ul>
  {/if}
</main>

<style>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    flex-flow: wrap;
  }
  li {
    width: 20%;
    margin-bottom: 20px;
  }
</style>
