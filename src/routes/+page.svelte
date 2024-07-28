<script>
    import { uiuisms } from '$lib/uiuisms';

    /**
     * @param {string} code
     * @param {{embed?: boolean}} flags
     */
    function pad(code, { embed } = { embed: false }) {
        const encoded = encodeURIComponent(code);
        console.log({ encoded });
        return `https://www.uiua.org/${embed ? 'embed' : 'pad'}?src=${encoded}`;
    }
</script>

<table class="table is-fullwidth is-striped is-hoverable is-narrow">
    <thead>
        <tr>
            <th> Name </th>
            <th> Code </th>
            <th> Pad </th>
        </tr>
    </thead>
    <tbody>
        {#each uiuisms as { name, code }}
            <tr>
                <td>
                    {name}
                </td>
                <td>
                    <iframe
                        src={pad(code, { embed: true })}
                        title={name}
                        width="100%"
                        height="40px"
                    >
                    </iframe>
                </td>
                <td><a href={pad(code)}>Pad</a></td>
            </tr>
        {/each}
    </tbody>
</table>
