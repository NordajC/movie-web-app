<script>
  let searchQuery = '';

  function handleSearch() {
    // Perform search logic here
    console.log('Search query:', searchQuery);
  }
</script>

<main>
  <h1>Welcome to the Movie App</h1>

  <div class="search-bar">
    <input type="text" bind:value={searchQuery} placeholder="Search movies..." />
    <button on:click={handleSearch}>Search</button>
  </div>

  <!-- Movie list goes here -->
</main>

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }

  .search-bar {
    display: flex;
    align-items: center;
    margin-top: 20px;
  }

  input {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-right: 10px;
  }

  button {
    padding: 10px 20px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
</style>
