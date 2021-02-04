<script>
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
    <input
      placeholder="Search a github user..."
      type="text"
      bind:value={query}
    />
    <button>Search</button>
  </form>
</div>

{#if user}
  <div class="userCard">
    <img src={user.avatar_url} alt="John" style="width:100%" />
    <h1>{user.login}</h1>
    <a href={user.html_url}><i class="fa fa-github" />Github Page</a>
  </div>
{/if}<link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css"
/>

<style>
  .user-search {
    padding: 20px;
    background: #eee;
    border-radius: 10px;
    margin-bottom: 40px;
  }
  .userCard {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    max-width: 300px;
    margin: auto;
    text-align: center;
    margin-bottom: 20px;
  }
  .userCard:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  }
  a {
    text-decoration: none;
    font-size: 22px;
    color: black;
  }
</style>
