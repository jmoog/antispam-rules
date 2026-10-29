# antispam-rules

Règles anti-spam **centralisées** pour les formulaires de devis des sites Astro
(LJ Couverture, Robert 94, etc. — `src/lib/antispam.ts`).

Chaque site lit `rules.json` via la variable d'environnement `SPAM_RULES_URL`
(cache 1 h par défaut, fallback sur les règles intégrées au code si l'URL est
injoignable). **Modifier un mot-clé ici suffit : aucun redéploiement des sites.**

## Format

- `threshold` : score à partir duquel la demande est rejetée en silence
- `keywords[]` : regex (`re`, `flags`), points (`pts`), étiquette de log (`label`)
- `phonePrefixes[]` : indicatifs téléphoniques suspects
- `english` : détection de message majoritairement anglophone

## Utilisation

```
SPAM_RULES_URL=https://raw.githubusercontent.com/jmoog/antispam-rules/main/rules.json
```

⚠️ Le dépôt doit être **public** pour que `raw.githubusercontent.com` soit accessible
sans authentification. Il ne contient aucune donnée sensible (de simples mots-clés).
Penser à incrémenter `version` à chaque modification (visible dans les logs).
