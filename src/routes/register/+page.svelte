<script context="module">
	export const prerender = true;
</script>

<script>
    let userId = '';
    let password = '';
    let email = '';
  
    const url = 'http://localhost:3000'

    async function handleSubmit(event) {
      event.preventDefault();
        try {
            const res = await fetch(`${url}/register`, {
              method: 'POST',              
              body: JSON.stringify({userId, password, email}),
              headers: {
                'Content-Type': 'application/json'
              }
            })
            console.log(res.status);
            if(res.status !== 204)
              throw res.status
            alert("registrazione effettuata")
            location.href = '/';
        } catch (error) {
            console.log(error);
            //TODO
            alert(error)
        }
    }
    
  
</script>

<form on:submit={handleSubmit}>
    <div>
      <label>
        User ID:
        <input type="text" bind:value={userId} />
      </label>
    </div>
    <div>
      <label>
        Password:
        <input type="password" bind:value={password} />
      </label>
    </div>
    <div>
      <label>
        Email:
        <input type="text" bind:value={email} />
      </label>
    </div>
    
    <button type="submit">Registrati</button>
    <nav>
        <ul>
          <li><a href="/">Sei già registrato?</a></li>
        </ul>
    </nav>
</form>

<style>
    div {
      margin-bottom: 10px;
    }
</style>