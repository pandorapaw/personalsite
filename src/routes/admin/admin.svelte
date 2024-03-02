<script lang="ts">
  import {pb} from '../../lib/pocketbase'
  export let user:string;

  function signOut() {
    pb.authStore.clear();
  }
</script>

<p>Signed in as {user}</p>
<button on:click={signOut}>Sign out</button>