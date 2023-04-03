<script context="module">
	export const prerender = true;

  //TODO remove JTW when you logout
</script>

<script>    
    let color = 'green';
    
    function handleClick() {
      color = color === 'green' ? 'red' : 'green';
    }
    function logout() {
      alert("Logout effettuato")
    }
</script>
  
<button style="background-color: {color}" on:click={handleClick}>
    Cambia colore
</button>
<nav>
    <ul>
      <li><a on:click={logout} href="/">Logout</a></li>
    </ul>
</nav>