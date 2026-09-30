# Projet partogramme

Suivi du travail en salle de naissance (TP avec données fictives). Site statique sans build ;
bibliothèques via CDN : supabase-js 2, chart.js 4 (courbe de dilatation), exceljs (export Excel).
`maquette.png` est le dessin de référence. Les onglets : Suivi du travail, Patientes, Grossesses,
Enfants, Praticiens (un fichier JS par onglet, `app.js` gère la navigation et les patientes).

## Base de données

- Projet Supabase : `ijyabacodmefufowphts` (connecté au MCP `supabase`).
- Tables : `patiente`, `grossesse`, `examen`, `enfant`, `praticien`, `orientation`.
- Énumérations PostgreSQL : `groupe_sanguin`, `specialite` (praticiens), `sexe` — à utiliser
  telles quelles dans les formulaires.
- RLS ouverte en lecture, ajout et modification (migration `ouvre_rls_tp_fictif`) car les
  données sont fictives. Ne pas y mettre de données réelles tant qu'elle est ouverte.

## config.js — attention

- `config.js` contient **seulement** l'URL du projet et la clé publishable. Jamais de clé
  secrète (`service_role` ou `secret`) : une clé secrète contournée toutes les protections RLS.
- Le fichier est normalement écrit par l'outil `Connecter-Supabase.bat` (dossier parent
  `CultureNum-L3SPS`). Une ancienne version contenait des clés secrètes collées à la suite de
  la clé publique (corrigé le 30/09/2026) : si les requêtes Supabase renvoient 401, vérifier
  d'abord ce fichier.

## Essayer en local

- Python n'est pas installé sur ce PC ; lancer plutôt :
  `npx.cmd -y http-server . -p 8765 -c-1` puis ouvrir http://localhost:8765/
  (utiliser `npx.cmd` et non `npx` : PowerShell refuse `npx.ps1` sur ce PC).

## Mise en ligne

- Adresse : https://sps-g36-parto.professeurpetitchat.com/
- Dépôt GitHub public : https://github.com/Paulo7120/partogramme (mis en ligne le 30/09/2026,
  workflow `deploy.yml` vérifié au clic).