<script lang="ts">
	import { currentUser } from "$lib/store";
    import { login, logout } from "$lib/utils/auth";

    let email = "";
    let password = "";

</script>
<section>

    {#if $currentUser}
        <h1>Logged in as {$currentUser.name}</h1>
        <button on:click={logout}>Logout</button>
    {/if}
    {#if !$currentUser}
        <h1>Not logged in</h1>
        <!--Disable form redirect-->
        <form on:submit|preventDefault>
            <h1>Connexion</h1>
            <div class="form-control w-full max-w-xs">
                <!-- svelte-ignore a11y-label-has-associated-control -->
                <input type="text" placeholder="Votre Email" class="input input-bordered w-full max-w-xs" bind:value={email} />
                <input type="password" placeholder="Mot de passe" class="input input-bordered w-full max-w-xs" bind:value={password} />
                <button type="submit" class="btn btn-primary" on:click={login(email,password)} >Se connecter</button>
            </div>
        </form>
    {/if}


</section>