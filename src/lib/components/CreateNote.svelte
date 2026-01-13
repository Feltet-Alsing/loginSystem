<script>
	import { createNote } from '$lib/db/notes.remote';
</script>

<div class="create-note-card">
	<h2>Create New Note</h2>
	<form {...createNote}>
		<label>
			<span>Title</span>
			<input {...createNote.fields.title.as('text')} placeholder="Enter note title" />
			{#each createNote.fields.title.issues() as issue}
				<p class="error">{issue.message}</p>
			{/each}
		</label>

		<label>
			<span>Content</span>
			<textarea {...createNote.fields.content.as('text')} placeholder="Write your note..."
			></textarea>
			{#each createNote.fields.content.issues() as issue}
				<p class="error">{issue.message}</p>
			{/each}
		</label>

		<button type="submit">Create Note</button>
	</form>
</div>

<style>
	.create-note-card {
		background: var(--light-grey);
		padding: 30px;
		border-radius: 12px;
		box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
	}

	h2 {
		color: var(--dark-grey);
		font-size: 22px;
		font-weight: 600;
		margin-bottom: 24px;
	}

	form {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}

	label {
		display: flex;
		flex-direction: column;
		gap: 8px;
	}

	label span {
		color: var(--dark-grey);
		font-size: 14px;
		font-weight: 500;
	}

	input,
	textarea {
		padding: 12px 16px;
		border: 1px solid var(--border-color);
		border-radius: 6px;
		font-size: 15px;
		background: white;
		color: var(--dark-grey);
		transition: all 0.2s;
		font-family: inherit;
	}

	textarea {
		min-height: 120px;
		resize: vertical;
	}

	input:focus,
	textarea:focus {
		outline: none;
		border-color: var(--medium-grey);
		box-shadow: 0 0 0 3px rgba(106, 106, 106, 0.1);
	}

	input::placeholder,
	textarea::placeholder {
		color: #aaa;
	}

	.error {
		color: var(--error-red);
		font-size: 13px;
		margin-top: -4px;
	}

	button {
		padding: 14px;
		background: var(--dark-grey);
		color: white;
		border: none;
		border-radius: 6px;
		font-size: 16px;
		font-weight: 500;
		cursor: pointer;
		transition: all 0.2s;
		margin-top: 8px;
	}

	button:hover {
		background: var(--medium-grey);
		transform: translateY(-1px);
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
	}

	button:active {
		transform: translateY(0);
	}
</style>
