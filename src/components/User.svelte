<script>
  export let username;
  export let avatar;
</script>

<img src={avatar} alt={`${username}'s avatar`} />
<h3>{username}</h3>

<style>
  img {
    max-width: 40px;
  }
  h3 {
    margin: 0;
  }
</style>
