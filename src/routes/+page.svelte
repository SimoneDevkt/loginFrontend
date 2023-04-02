<script context="module">
	export const prerender = true;
</script>

<form name="form-example" data-netlify="true">
    <input type="hidden" name="form-name" />
    <label for="name">Name</label>
    <input name="name" id="name" required placeholder="Name" type="text" />
    <label for="email">Email</label>
    <input name="email" id="email" required placeholder="Email" type="email" />
    <label for="message">Message</label>
    <input name="message" id="message" required placeholder="Message" type="text" />
    <input type="submit" value="Submit" />
</form>