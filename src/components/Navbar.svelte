<script lang="ts">
    import { supabase } from "$lib/supabase";

    function logout() {
        supabase.auth.signOut();
    }
</script>

<div class="my-4 flex justify-end">
    <button
        on:click={logout}
        class="shadow-sm rounded bg-blue-500 hover:bg-blue-600 py-2 px-4 text-white"
        >Log out</button
    >
</div>
