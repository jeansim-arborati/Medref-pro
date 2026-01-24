# MedRef Pro - Fiches Médicales Professionnelles

Application PWA de fiches médicales générées et actualisées par IA (Claude), avec synchronisation cloud via GitHub Gist.

## 🚀 Installation rapide

### 1. Héberger sur GitHub Pages

1. Créez un nouveau repository sur GitHub
2. Uploadez ces fichiers : `index.html`, `manifest.json`, `icon-192.png`, `icon-512.png`
3. Allez dans **Settings** → **Pages**
4. Sélectionnez la branche `main` et le dossier `/ (root)`
5. Votre app sera disponible à `https://votre-username.github.io/votre-repo/`

### 2. Configurer le Proxy Cloudflare (résout l'erreur 400)

L'API Anthropic bloque les appels directs depuis un navigateur. Le proxy Cloudflare est **gratuit** et résout ce problème.

1. Allez sur [dash.cloudflare.com](https://dash.cloudflare.com)
2. Créez un compte gratuit si nécessaire
3. **Workers & Pages** → **Create application** → **Create Worker**
4. Nommez-le `medref-proxy` → **Deploy**
5. **Edit code** → Collez le contenu de `cloudflare-worker.js`
6. **Save and Deploy**
7. Copiez l'URL du worker (ex: `medref-proxy.votre-compte.workers.dev`)

### 3. Activer le proxy dans l'app

Modifiez `index.html` (lignes ~530) :

```javascript
const PROXY_URL = 'https://medref-proxy.VOTRE_COMPTE.workers.dev';
const USE_PROXY = true;  // Changez de false à true
```

Re-uploadez le fichier sur GitHub.

### 4. Configurer l'API Anthropic

1. Obtenez une clé API sur [console.anthropic.com](https://console.anthropic.com)
2. Dans l'app, cliquez sur l'icône ⚙️ (paramètres)
3. Entrez votre clé API
4. Cliquez **Enregistrer**

### 5. Installer sur iPhone

1. Ouvrez l'URL de votre app dans Safari
2. Appuyez sur **Partager** (icône carré avec flèche)
3. **Sur l'écran d'accueil**
4. Nommez l'app → **Ajouter**

---

## ☁️ Synchronisation entre appareils (GitHub Gist)

Pour synchroniser vos fiches entre plusieurs appareils :

### Créer un token GitHub

1. Allez sur [github.com/settings/tokens](https://github.com/settings/tokens)
2. **Generate new token (classic)**
3. Nommez-le "MedRef Pro"
4. Cochez uniquement **gist**
5. **Generate token**
6. **Copiez le token** (il ne sera plus visible après)

### Configurer dans l'app

1. Ouvrez les paramètres (⚙️)
2. Entrez le token dans **Token GitHub**
3. Laissez **Gist ID** vide (sera auto-généré)
4. **Enregistrer**

### Utilisation

- **Icône sync (↻)** dans le header : sauvegarde vers GitHub
- **Charger depuis GitHub** : récupère les fiches sur un nouvel appareil

---

## 📱 Fonctionnalités

- ✅ **70+ pathologies** couvrant 90% des cas en médecine occidentale
- ✅ **Fiches complètes** : définition, épidémiologie, physiopathologie détaillée, symptômes, diagnostic, traitement
- ✅ **Mnémotechniques** pour mémoriser chaque pathologie
- ✅ **Mise à jour IA** : actualise les fiches avec les dernières recommandations
- ✅ **Mode hors ligne** : fiches accessibles sans connexion une fois générées
- ✅ **Sync cloud** : vos données sur tous vos appareils
- ✅ **Design responsive** : parfait sur iPhone, iPad et desktop

---

## 💰 Coûts

| Service | Coût |
|---------|------|
| GitHub Pages | Gratuit |
| Cloudflare Workers | Gratuit (100K requêtes/jour) |
| GitHub Gist | Gratuit |
| **API Anthropic** | ~$0.003/fiche (~$0.20 pour les 70 fiches) |

---

## 🔧 Dépannage

### Erreur 400 / API Error
→ Le proxy n'est pas configuré. Suivez l'étape 2 et 3.

### La clé API ne fonctionne pas
→ Vérifiez sur console.anthropic.com que vous avez du crédit et que la clé est active.

### Les fiches ne se synchronisent pas
→ Vérifiez que le token GitHub a bien le scope "gist".

### L'app ne s'installe pas sur iPhone
→ Utilisez Safari (pas Chrome). L'option est dans Partager → Sur l'écran d'accueil.

---

## 📄 Fichiers

| Fichier | Description |
|---------|-------------|
| `index.html` | Application complète (à uploader sur GitHub) |
| `manifest.json` | Configuration PWA (à uploader) |
| `icon-192.png` | Icône 192x192 (à uploader) |
| `icon-512.png` | Icône 512x512 (à uploader) |
| `cloudflare-worker.js` | Code du proxy (à déployer sur Cloudflare) |

---

## 📞 Support

En cas de problème, vérifiez :
1. La console du navigateur (F12 → Console) pour les erreurs
2. Que le proxy Cloudflare est bien déployé et accessible
3. Que les clés API sont correctement entrées
