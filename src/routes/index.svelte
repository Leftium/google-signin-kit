<script>
    import { onMount } from 'svelte'

    const clientId = import.meta.env.VITE_CLIENT_ID;

    onMount(async () => {
        const handleCredentialResponse = async (response) => {
            console.log('Encoded JWT ID token: ' + response.credential);
            };
        google.accounts.id.initialize({
            client_id: clientId,
            callback: handleCredentialResponse,
        });
        google.accounts.id.renderButton(
            document.getElementById('buttonDiv'),
            { theme: 'outline', size: 'large' } // customization attributes
        );
        google.accounts.id.prompt();
    });

</script>

<svelte:head>
    <script src="https://accounts.google.com/gsi/client" async defer></script>
</svelte:head>

<div id=buttonDiv></div>
