<script context="module">
	export const prerender = true;
</script>

<script>
    let userId = '';
    let password = '';

    const url = 'http://localhost:3000'
  
    async function login(event) {
        event.preventDefault();      
        try {
            const res = await fetch(`${url}/login`, {
              method: 'POST',              
              body: JSON.stringify({userId, password}),
              headers: {
                'Content-Type': 'application/json'
              }
            })
            if(res.status !== 201)
              throw res.status
            //TODO save JTW that you receive in the response
            location.href = '/app';
        } catch (error) {
            console.log(error);
            //TODO
            alert('Wrong password')
        }
    }
</script>

<form on:submit={login}>
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
    <button type="submit">Accedi</button>
    <nav>
        <ul>
          <li><a href="/register">Non sei ancora registrato?</a></li>
          <li><a href="/resetpassword">Password dimenticata?</a></li>
        </ul>
    </nav>
</form>

<style>
    div {
      margin-bottom: 10px;
    }
</style>