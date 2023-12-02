<!-- Java Script -->
<script>
	// components from svelte that are used for animation
    import AnimatedHeader from "../AnimatedHeader.svelte"
	import { quintOut } from 'svelte/easing';
	import { crossfade } from 'svelte/transition';
	import { flip } from 'svelte/animate';



	// the animation
	const [send, receive] = crossfade({
		// @ts-ignore
		fallback(node, params) {
			const style = getComputedStyle(node);
			const transform = style.transform === 'none' ? '' : style.transform;

			return {
				duration: 600,
				easing: quintOut,
				css: (t) => `
					transform: ${transform} scale(${t});
					opacity: ${t}
				`
			};
		}
	});

	let todos = [
		{ id: 1, done: true, description: 'Create Powerpoint' },
		{ id: 2, done: true, description: 'Create Sample Page' },
		{ id: 3, done: false, description: 'Present to the class'},
		{ id: 4, done: false, description: 'Fix some bugs'},
		{ id: 5, done: false, description: 'Make GitHub page'},
		{ id: 6, done: false, description: 'Add Documentation'}
	];

	let uid = todos.length + 1;

	/**
     * @param {EventTarget | null} input
     */
	function add(input) {
		const todo = {
			id: uid++,
			done: false,
			// @ts-ignore
			description: input.value
		};

		todos = [todo, ...todos];
		// @ts-ignore
		input.value = '';
	}

	// @ts-ignore
	function remove(todo) {
		todos = todos.filter((t) => t !== todo);
	}
</script>



<!-- CSS -->
<style>
	.new-todo {
		font-size: 1.4em;
		width: 100%;
		margin: 2em 0 1em 0;
	}

	.board {
		max-width: 36em;
		margin: 0 auto;
	}

	.left,
	.right {
		float: left;
		width: 50%;
		padding: 0 1em 0 0;
		box-sizing: border-box;
	}

	h2 {
		font-size: 2em;
		font-weight: 200;
		user-select: none;
	}

	label {
		top: 0;
		left: 0;
		display: block;
		font-size: 1em;
		line-height: 1;
		padding: 0.5em;
		margin: 0 auto 0.5em auto;
		border-radius: 2px;
		background-color: #e3ebf1;
		user-select: none;
		color: black;
	}

	input {
		margin: 0;
	}

	.right label {
		background-color: #ffb8a2;
	}

	button {
		float: right;
		height: 1em;
		box-sizing: border-box;
		padding: 0 0.5em;
		line-height: 1;
		background-color: transparent;
		border: none;
		color: rgb(170, 30, 30);
		opacity: 0;
		transition: opacity 0.2s;
	}

	label:hover button {
		opacity: 1;
	}
</style>



<!-- HTML -->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sample</title>
</head>
<div>
    <AnimatedHeader selected="sample" />

    <div class="board">

        <input
            class="new-todo"
            placeholder="what needs to be done?"
            on:keydown={(event) => event.key === 'Enter' && add(event.target)}
        />

        <div class="left">
            <h2>todo</h2>
            {#each todos.filter((t) => !t.done) as todo (todo.id)}
                <label in:receive={{ key: todo.id }} out:send={{ key: todo.id }} animate:flip>
                    <input type="checkbox" bind:checked={todo.done} />
                    {todo.description}
                    <button on:click={() => remove(todo)}>x</button>
                </label>
            {/each}
        </div>

        <div class="right">
            <h2>done</h2>
            {#each todos.filter((t) => t.done) as todo (todo.id)}
                <label in:receive={{ key: todo.id }} out:send={{ key: todo.id }} animate:flip>
                    <input type="checkbox" bind:checked={todo.done} />
                    {todo.description}
                    <button on:click={() => remove(todo)}>x</button>
                </label>
            {/each}
        </div>
    </div>
</div>
</html>