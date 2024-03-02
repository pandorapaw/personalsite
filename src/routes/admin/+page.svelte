<script lang="ts">
  import {currentUser, pb} from '../../lib/pocketbase'
  import Admin from './admin.svelte'
  let email: string;
  let password: string;

  async function login() {
    await pb.admins.authWithPassword(email,password);
  }
</script>

{#if $currentUser}
 <Admin user={$currentUser.email}/>
{:else}
<form on:submit|preventDefault>
  <input placeholder="Email" type="text" bind:value={email}/>
  <input placeholder="Password" type="password" bind:value={password}/>
  <button on:click={login}>Login</button>
</form>
{/if}