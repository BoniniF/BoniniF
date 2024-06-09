<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <title>Visualizzatore di Testo</title>
</head>
<body>
    <h1>Visualizzatore di Testo</h1>
    <p id="text-display"></p>

    <script>
        // Funzione per ottenere il parametro <your_text> dall'URL
        function getYourText() {
            const url = window.location.href;
            const match = url.match(/rj1nsngsbou77t0ra\/(.+)/);
            return match ? decodeURIComponent(match[1]) : null;
        }

        // Funzione per mostrare il testo a schermo
        function displayText() {
            const yourText = getYourText();
            if (yourText) {
                document.getElementById('text-display').textContent = yourText;
                updateGitHubReadMe(yourText);
            } else {
                document.getElementById('text-display').textContent = 'Nessun testo fornito.';
            }
        }

        // Funzione per aggiornare il README su GitHub
        async function updateGitHubReadMe(text) {
            const githubToken = 'YOUR_GITHUB_TOKEN'; // Sostituire con il proprio token GitHub
            const repo = 'BoniniF/BoniniF';
            const path = 'README.md';

            // Ottenere il contenuto attuale del README
            const response = await fetch(`https://api.github.com/repos/${repo}/contents/${path}`, {
                headers: {
                    'Authorization': `token ${githubToken}`
                }
            });
            const data = await response.json();
            const content = atob(data.content);
            const newContent = content + '\n' + text;
            const sha = data.sha;

            // Aggiornare il contenuto del README
            await fetch(`https://api.github.com/repos/${repo}/contents/${path}`, {
                method: 'PUT',
                headers: {
                    'Authorization': `token ${githubToken}`,
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    message: 'Aggiornamento README.md',
                    content: btoa(newContent),
                    sha: sha
                })
            });
        }

        // Mostrare il testo a schermo
        displayText();
    </script>
</body>
</html>
