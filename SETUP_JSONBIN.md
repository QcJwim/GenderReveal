# Configuration JSONBin.io

## Étapes pour configurer la base de données

### 1. Créer un compte JSONBin.io
- Allez sur https://jsonbin.io
- Inscrivez-vous gratuitement (GitHub ou email)

### 2. Créer une nouvelle collection
- Cliquez sur "New Bin"
- Choisissez "Collection" comme type
- Copiez le **Bin ID** (dans l'URL, ex: `https://api.jsonbin.io/v3/c/BIN_ID_HERE`)
- Copiez le **API Key** depuis votre profil (Settings > API Key)

### 3. Configurer le code

Ouvrez `index.html` et remplacez ces lignes (lignes 497-499):

```javascript
const JSONBIN_API_KEY = '$2a$10$YOUR_API_KEY_HERE';
const JSONBIN_BIN_ID = 'YOUR_BIN_ID_HERE';
```

Par vos vraies valeurs:

```javascript
const JSONBIN_API_KEY = '$2a$10$votre_cle_api_real';
const JSONBIN_BIN_ID = 'votre_bin_id';
```

**Faites la même chose dans `admin.html` (lignes 310-311).**

### 4. Initialiser la base de données

Avec l'API Key et Bin ID configurés, exécutez cette commande curl (ou via Postman) pour initialiser la structure:

```bash
curl -X PUT https://api.jsonbin.io/v3/b/VOTRE_BIN_ID \
  -H "Content-Type: application/json" \
  -H "X-Access-Key: VOTRE_API_KEY" \
  -d '{"guests": []}'
```

Ou simplement ouvrez `index.html` dans votre navigateur et soumettez une inscription - la base sera créée automatiquement au premier envoi.

### 5. Règles de sécurité (optionnel)

Dans JSONBin.io, vous pouvez:
- Rendre le bin **privé** (seul votre API Key y accède)
- Définir des règles d'expiration

---

## Format des données

Les données sont stockées ainsi:

```json
{
  "guests": [
    {
      "id": 1712345678900,
      "names": ["Marie Dupont", "Jean Tremblay"],
      "timestamp": "15/04/2026 14:30"
    }
  ]
}
```
