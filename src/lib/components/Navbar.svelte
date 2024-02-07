<script>
import SearchBar from "./SearchBar.svelte";
import Links from "./Links.svelte";
</script>
<nav>
  <div class="search-bar">
    <Links/>
    <SearchBar/>
  </div>
</nav>


<style>
  nav {
    display: flex;
    justify-content: space-between;
    padding: 20px;
    background-color: #648DB6;
    box-shadow: 0 2px 4px rgba(15, 10, 85, 0.1);
    width: 100%;
  }
  .search-bar {
    
    display: flex;
    justify-content: flex-end;
    align-items: left;
  }
</style>