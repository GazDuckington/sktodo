<script lang="ts">
    import "../app.css";
    import { loadTodos } from "../stores/todoStore";
    import Auth from "../components/Auth.svelte";
    import Navbar from "../components/Navbar.svelte";
    import { user } from "../stores/authStore";
    import { supabase } from "$lib/supabase";

    user.set(supabase.auth.user());

    supabase.auth.onAuthStateChange((_, session) => {
        user.set(session?.user);
        if (session?.user) {
            loadTodos();
        }
    });
</script>

<div class="content">
    {#if $user}
        <Navbar />
        <slot />
    {:else}
        <Auth />
    {/if}
</div>

<style lang="postcss">
    .content {
        @apply container mx-auto my-6 max-w-lg;
    }
</style>
