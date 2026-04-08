# 🤖 BotForge — Discord Bot Control Panel

Panneau de contrôle web pour héberger et gérer vos bots Discord, avec base de données SQLite3.

## 🚀 Installation rapide

### 1. Prérequis
- Node.js 18+ : https://nodejs.org
- Un token de bot Discord : https://discord.com/developers/applications

### 2. Installer les dépendances
```bash
cd discord-bot-panel
npm install
```

### 3. Démarrer le serveur
```bash
npm start
```

### 4. Ouvrir dans le navigateur
```
http://localhost:3000
```

---

## 📋 Fonctionnalités

- ✅ **Création de compte** sécurisée (bcrypt, sessions)
- ✅ **Gestion multi-bots** — plusieurs bots par compte
- ✅ **Démarrage/Arrêt/Redémarrage** en un clic
- ✅ **Commandes personnalisées** — ajoutez des commandes via l'interface
- ✅ **Logs en temps réel** — rafraîchissement automatique toutes les 5s
- ✅ **Statistiques** — serveurs, uptime, utilisation des commandes
- ✅ **Stockage SQLite3** — base de données locale, aucun serveur externe requis
- ✅ **Interface dark mode** — design Discord-inspired

---

## 🗄️ Structure de la base de données (SQLite3)

| Table | Description |
|-------|-------------|
| `users` | Comptes utilisateurs (username, email, password hashé) |
| `bots` | Bots Discord (token, préfixe, statut) |
| `bot_commands` | Commandes personnalisées par bot |
| `bot_logs` | Historique des événements |

---

## 📁 Structure du projet

```
discord-bot-panel/
├── server.js          # Backend Express + Discord.js + SQLite
├── package.json       # Dépendances
├── botpanel.db        # Base SQLite3 (créée au démarrage)
└── public/
    └── index.html     # Frontend SPA
```

---

## 🔧 Créer un bot Discord

1. Aller sur https://discord.com/developers/applications
2. Créer une application → onglet **Bot**
3. Copier le **Token**
4. Activer **Message Content Intent** (Privileged Gateway Intents)
5. Inviter le bot sur votre serveur via OAuth2 → URL Generator

---

## 🔒 Sécurité en production

- Changez `express-session` secret dans `server.js`
- Utilisez HTTPS
- Ajoutez un fichier `.env` pour les secrets :
  ```
  SESSION_SECRET=votre_secret_ultra_long
  PORT=3000
  ```

---

## 🧩 Commandes Discord supportées

Les bots créés via le panel répondent aux commandes personnalisées créées dans l'interface.
Exemple : préfixe `!` + commande `aide` → le bot répond avec la réponse configurée.
