# DACK_Trad

Traducteur **Français / Anglais / Espagnol ⇄ Éwé** : dictée vocale, lecture vocale (y compris en éwé), conversion des nombres hors connexion.

Application 100 % statique (un seul fichier `index.html`), compatible **Edge, Chrome et Safari** (ordinateur, iPhone, iPad, Android).

## Mise en ligne sur GitHub Pages

1. Crée un dépôt GitHub (ex. `dack-trad`) et envoie-y les fichiers de ce dossier (`index.html`, `README.md`, `.nojekyll`).
2. Dans le dépôt : **Settings → Pages → Build and deployment**.
3. *Source* : **Deploy from a branch** · Branch : **main** · Dossier : **/ (root)** → **Save**.
4. Après ~1 minute, l'application est disponible sur `https://<ton-compte>.github.io/<nom-du-depot>/`.

Le site est servi en HTTPS, ce qui est nécessaire pour la dictée, le micro et la voix éwé : le fichier `lancer_serveur.bat` n'est donc plus utile.

## Compatibilité navigateurs

| Fonction | Chrome | Edge | Safari |
|---|---|---|---|
| Traduction (Google Translate) | ✅ | ✅ | ✅ |
| Nombres éwé ⇄ chiffres | ✅ | ✅ | ✅ |
| Lecture vocale FR / EN / ES | ✅ | ✅ | ✅ |
| Voix éwé (modèle MMS dans le navigateur) | ✅ | ✅ | ✅ (voir note) |
| Dictée vocale | ✅ | ✅ | ✅ Safari 14.1+ |

Notes :
- **Voix éwé** : téléchargement unique d'environ 114 Mo, conservé dans le navigateur (IndexedDB). Sur iPhone/iPad, la mémoire limitée peut faire échouer le chargement ; Safari peut aussi vider ce stockage après quelques jours sans visite (sauf si le site est ajouté à l'écran d'accueil / au Dock). Le modèle est alors simplement re-téléchargé.
- **Dictée** : le navigateur demande l'autorisation du micro ; elle est indisponible dans le sens Éwé → autres langues.
- Le premier son (lecture automatique) n'est possible qu'après un premier clic/toucher, règle imposée par Safari.

## Services externes utilisés

- Traduction : `translate.googleapis.com` (point d'accès public non officiel de Google Translate, soumis à des limites ; l'application gère les pauses automatiquement).
- Moteur audio : `onnxruntime-web` via jsDelivr.
- Voix éwé : modèle MMS-TTS de Meta (licence **CC-BY-NC**, usage non commercial) hébergé sur Hugging Face (`willwade/mms-tts-multilingual-models-onnx`).

Aucune donnée n'est stockée sur un serveur à toi : le cache des traductions reste dans le navigateur de chaque utilisateur.
