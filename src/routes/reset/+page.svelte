<script context="module">
	export const prerender = true;
</script>

<script>
    import { page } from '$app/stores'
    
    const token = $page.url.searchParams.get('token')
    console.log(token);

    let password = '';
    const url = 'http://localhost:3000'
    async function handleSubmit(event) {
      event.preventDefault();
      
      try {
            const res = await fetch(`${url}/reset`, {
              method: 'POST',
              body: JSON.stringify({password}),
              headers: {
                Authorization: `Bearer ${token}`,
                'Content-Type': 'application/json'
              }
            })
            console.log(res.status);
            if(res.status !== 204)
              throw res.status
            alert("password resettata")
            location.href = '/';
        } catch (error) {
            console.log(error);
            //TODO
            alert("utente non trovato")
        }
      // qui inserisci la logica per verificare l'autenticazione utente
    }
</script>

<form on:submit={handleSubmit}>
    <div>
      <label>
        Password:
        <input type="password" bind:value={password} />
      </label>
    </div>
    <button type="submit">Resetta password</button>
</form>

<style>
    div {
      margin-bottom: 10px;
    }
</style>