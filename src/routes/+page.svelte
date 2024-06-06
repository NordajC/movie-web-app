<script>
    import Navbar from '../lib/components/Navbar.svelte';
    // const apiKey = process.env.API_KEY;
    // console.log(apiKey);
    let fileContents = '';

  fetch('api_key.txt')
    .then(response => response.text())
    .then(data => {
      fileContents = data;
    });
</script>

<main>
    <Navbar />
    <h1>Welcome to the Movie App</h1>

    

    <!-- Movie list goes here -->
</main>