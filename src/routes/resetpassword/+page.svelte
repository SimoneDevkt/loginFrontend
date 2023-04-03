<script context="module">
	export const prerender = true;
</script>

<script>
    let userId = '';
    const url = 'http://localhost:3000'
    async function handleSubmit(event) {
      event.preventDefault();
      
      try {
            const res = await fetch(`${url}/recover`, {
              method: 'POST',
              body: JSON.stringify({userId}),
              headers: {
                'Content-Type': 'application/json'
              }
            })
            console.log(res.status);
            if(res.status !== 204)
              throw res.status
            alert("mail inviata, controlla la cartella spam")
            //location.href = '/';
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
        User ID:
        <input type="text" bind:value={userId} />
      </label>
    </div>
    <button type="submit">Recupera password</button>
    <nav>
        <ul>
          <li><a href="/">Indietro</a></li>
        </ul>
    </nav>
</form>

<style>
    div {
      margin-bottom: 10px;
    }
</style>