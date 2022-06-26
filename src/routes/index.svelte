<script lang="ts">
    import TodoForm from "../components/TodoForm.svelte";
    import Todo from "../components/Todo.svelte";
    import { todos } from "../stores/todoStore";
</script>

<title>Todos</title>
<main>
    <h1 class="text-2xl font-bold text-center text-gray-800 md:text-3xl">
        my Todos:
    </h1>
    <TodoForm />
    {#each $todos as todo}
        <Todo {todo} />
    {/each}
</main>
