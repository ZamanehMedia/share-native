<script lang="ts">
    import Card from './Card.svelte';

    const placeholders = {
        title: 'Discover Native Share',
        text: 'The share() method of the Navigator interface invokes the native sharing mechanism of the device to share data such as text, URLs, or files. The available share targets depend on the device, but might include the clipboard, contacts and email applications, websites, Bluetooth, etc.',
        url: 'https://developer.mozilla.org/en-US/docs/Web/API/Navigator/share',
        files: []
    }

    let payload = {
        title: '',
        text: '',
        url: '',
        files: []
    }
</script>

<article>
    <h1>Discover Native Share</h1>
    <label for="title-editor">Title</label>
    <input name="title-editor" id="title-editor" type="text" bind:value={payload.title} placeholder={placeholders.title} />
    <label for="text-editor">Text</label>
    <input name="text-editor" id="text-editor" type="text" bind:value={payload.text} placeholder={placeholders.text} />
    <label for="url-editor">URL</label>
    <input name="url-editor" id="text" bind:value={payload.url} placeholder={placeholders.url} />
</article>

<section>
    <Card title="Files">
        {typeof(payload.files)} {payload.files} {payload.files.length}
        {#if payload.files.length > 0}
        <ul>
            {#each payload.files as file}
            <li>{file.name}</li>
            {/each}
        </ul>
        {/if}
        <label for="file-selector"><a><em>Select files</em></a></label>
        <input name="file-selector" id="file-selector" bind:files={payload.files} multiple type="file" class="hidden">
    </Card>
    <Card title="Analysis">

    </Card>
    <Card title="Instructions">

    </Card>
</section>

<article>
    <details>
        <summary>Parsed result</summary>
        <pre><code id="parsed-payload">{JSON.stringify(payload, null, 2)}</code></pre>
    </details>
    <details>
        <summary>Manually craft your payload</summary>
        <p>You can manually craft your payload prior to sharing.</p>
        <label for="payload-editor">Payload</label>
        <textarea placeholder="{JSON.stringify(placeholders, null, 2)}" rows="10" disabled />
    </details>
</article>

<section>
    <button id="share-button" disabled>Share ↗</button>
</section>

<style>
    .hidden {
        display: none;
    }
</style>
