<script lang="ts">
    import { supabase } from "$lib/supabase";

    let loading = true;
    let email: string;

    async function handleLogin() {
        try {
            console.log(email);
            const { error } = await supabase.auth.signIn({ email });

            if (error) throw error;
            alert("Check your email for the login link!");
        } catch (error: any) {
            console.error(error);
            alert(error.error_description || error.message);
        } finally {
            loading = false;
        }
    }
</script>

<h1 class="text-2xl font-bold text-center text-gray-800 md:text-3xl">Log In</h1>
<p class="text-center mt-2">Sign In with magic link</p>

<form on:submit|preventDefault={handleLogin}>
    <div class="flex flex-col text-sm mb-2">
        <label class="font-bold mb-2 text-gray-800" for="email">Email</label>
        <input
            class="appearance-none shadow-sm border border-gray-200 p-2 focus:outline-none
        focus:border-gray-500 rounded-lg"
            type="email"
            name="email"
            placeholder="your@email.com"
            bind:value={email}
        />
    </div>
    <button
        type="submit"
        class="w-full shadow-sm rounded bg-blue-500 hover:bg-blue-600 text-white py-2 px-4"
        >Log In</button
    >
</form>
