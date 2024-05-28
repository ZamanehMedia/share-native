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
    <input type="text" bind:value={payload.title} placeholder={placeholders.title} />
    <label for="text-editor">Text</label>
    <input type="text" bind:value={payload.text} placeholder={placeholders.text} />
    <label for="url-editor">URL</label>
    <input type="text" bind:value={payload.url} placeholder={placeholders.url} />
</article>

<section>
    <Card title="Files">
        <input bind:value={payload.files} multiple type="file">
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
