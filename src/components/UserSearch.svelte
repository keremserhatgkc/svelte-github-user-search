<script>
  import User from "./User.svelte";

  let user;
  let query = "";
  const handleSubmit = () => {
    fetch(`https://api.github.com/users/${query}`)
      .then(res => res.json())
      .then(data => {
        user = data;
      });
  };
</script>

<div class="user-search">
  <form on:submit|preventDefault={handleSubmit}>
    <input type="text" bind:value={query} />
    <button>Search</button>
  </form>
</div>

{#if user}
  <div class="result">
    <User username={user.login} avatar={user.avatar_url} />
  </div>
{/if}

<style>
  .user-search {
    padding: 20px;
    background: #eee;
    border-radius: 10px;
    margin-bottom: 40px;
  }
  .result {
    padding: 10px;
    display: flex;
    flex-direction: column;
    position: relative;
    width: 50px;
    width: auto;
    margin-bottom: 20px;
    align-items: center;
  }
</style>
