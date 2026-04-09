# CORTEX by No Limit Academy — Instructions Claude Code

## Contexte

CORTEX est la plateforme d'intelligence santé de précision de No Limit Academy. Ecosystème SaaS complet avec 6 agents IA spécialisés, 137 biomarqueurs, intégration wearables via Terra API, boutique partenaires avec Stripe Connect, et back office admin.

Fondateurs : Johann Langenberg (ancien n°1 mondial, 5x champion d'Europe, expert tech/IA/vidéo) et Dustin Arnold (ancien champion de boxe, fondateur NATICS Bois-Guillaume, méthode IMPACT/FLOW/VISION).

**Positionnement : premium mais accessible. PAS exclusivement dirigeants. Ne JAMAIS utiliser "dirigeants" comme cible unique. Ne JAMAIS mentionner "roller" pour Johann.**

## Notion — Documentation complète

Toujours consulter ces pages Notion pour le contexte détaillé :

- Hub projet : https://www.notion.so/33cd8049714c8170a93beece19be1222
- Instructions Claude Code V3 : https://www.notion.so/33dd8049714c810aaed1f3ae38030c39
- Architecture Agents IA V2 : https://www.notion.so/33dd8049714c81348780fb1be6268e87
- Data Pipeline : https://www.notion.so/33dd8049714c813d8986ce6788887aaa
- Connecteurs santé : https://www.notion.so/33dd8049714c814eab39d9b6704da736
- Questionnaire Onboarding : https://www.notion.so/33dd8049714c81a3ad8aef788b810449
- DA V2 Monochrome Luxe : https://www.notion.so/33dd8049714c8146ba85e3c78e71d014
- Page présentation App : https://www.notion.so/33dd8049714c8172bc49f0d596919cae

## Stack technique

- **Frontend** : Astro 5 + React islands
- **Backend** : Supabase (projet: vtamvepxwntxzmpmzwqu, région: eu-west-3 Paris)
- **Paiements** : Stripe + Stripe Connect (commissions partenaires)
- **Deploy** : Netlify (site ID: 367a9267-dac6-405e-bc72-7b544d310535)
- **DNS** : Cloudflare
- **Emails** : Resend
- **Workflows** : n8n (ikonik-ac.app.n8n.cloud)
- **Wearables** : Terra API (500+ devices)
- **IA** : Claude API (Anthropic) — moteur des 6 agents
- **Repo** : GitHub webflowjohann-prog/no-limit-academy

## Direction artistique — CRITIQUE

### Palette MONOCHROME + OR uniquement
```
#0D0D0D — fond principal
#262626 — cartes, surfaces
#595959 — texte secondaire
#A6A6A6 — texte tertiaire
#D9D9D9 — séparateurs
#FFFFFF — texte principal
#c9a96e — or NLA, SEULE couleur d'accent
#b8963e — or hover
```

**AUCUNE autre couleur.** Pas de vert, rouge, bleu, pastels.

### Typographie
- Titres : Playfair Display 400, italic or pour les accents
- Corps : DM Sans 300-400
- Labels : DM Sans 500, 9-10px, UPPERCASE, letter-spacing 0.15em
- Scores : Playfair Display 300, 48-72px, or

### Règles absolues
1. **ZÉRO emoji** dans toute l'application (amateur, détruit le luxe)
2. ZÉRO couleur autre que monochrome + or
3. Photos B&W en en-tête de chaque page agent
4. Dark mode UNIQUE (pas de mode clair)
5. Glassmorphism dark : rgba(38,38,38,0.6), backdrop-blur 24px
6. Coins 20-24px, ombres 0 8px 32px rgba(0,0,0,0.4)

### Photos B&W par agent
- FORGE : athlète sprinter / battle ropes / course piste
- MORPHÉE : océan noir / plage sable volcanique
- FUEL : capsules fond noir
- ZÉNITH : cerveau dans les mains
- ATLAS : sommet montagne dans les nuages
- ORACLE : gouttes eau macro surface noire

## Les 6 agents CORTEX

| Agent | Rôle | Données sources |
|---|---|---|
| FORGE | Entraînement, force, endurance, récupération | HRV, FC, cortisol, testostérone, charge |
| MORPHÉE | Sommeil, cycles, chronobiologie | Sleep score, deep/REM, HRV nuit, temp, SpO2 |
| FUEL | Nutrition, suppléments, hydratation | Biomarqueurs, carences, médications (ANSM) |
| ZÉNITH | Mental, stress, breathwork, méditation | HRV, stress score, journal humeur |
| ATLAS | Expériences, expéditions, préparation | CORTEX Score, validation biométrique |
| ORACLE | Intelligence, score, rapports, coordination | Toutes les données, calcul score |

## Supabase — 21 tables (migrations appliquées)

Tables principales : members, device_connections, daily_metrics, biomarker_knowledge (137 marqueurs insérés), biomarker_results, cortex_scores, partners, partner_products, agent_prescriptions, nutrition_profiles, experience_catalog, experience_validations, experience_bookings, member_compliance, agent_conversations, reports, partner_orders, member_health_profiles, onboarding_responses.

RLS activé sur toutes les tables. 15 index de performance.

## Connecteurs santé (France-first)

Hiérarchie CRITIQUE : sources françaises TOUJOURS en premier.
1. Terra API (wearables)
2. Table Ciqual ANSES (nutrition FR, PRIORITAIRE)
3. USDA FoodData (complément)
4. BDPM ANSM/HAS (médicaments FR, PRIORITAIRE)
5. Thésaurus ANSM (interactions)
6. Recommandations HAS
7. ANSES ANC (valeurs nutritionnelles FR)
8. PubMed (complément)

## Fonctionnalités critiques à développer

1. **Boutique suppléments avec bundles** — FUEL prescrit N suppléments, panier modifiable, Stripe Connect
2. **Plans multi-horizons** — jour/semaine/mois adaptatifs par FORGE
3. **Questionnaire mensuel** — 10-15 questions pour recalibrer
4. **Sync wearables Terra API** — webhook → n8n → Supabase
5. **Pré-réservation expériences** — quota minimum, remboursement auto, validation biométrique
6. **Back office admin** — vue globale, analytics business, modération
7. **Chat interne + push** — chat par agent (Claude API) + notifications push PWA
8. **Scanner OCR** — caméra → Claude Vision → extraction → matching 137 biomarqueurs

## Phase 1 MVP (priorité)

1. Landing page CORTEX (FAIT)
2. Auth Supabase (inscription, login, magic link)
3. Onboarding questionnaire 65 questions
4. Dashboard Home avec CORTEX Score
5. Agent FUEL (suppléments + boutique Stripe)
6. Agent MORPHÉE (analyse sommeil)
7. Scanner OCR biomarqueurs
8. Sync 1 wearable via Terra API
9. Chat IA par agent (Claude API)
10. PWA mobile

## Pattern déploiement IKONIK V5

1. Build séparé (pas de build auto Netlify)
2. Test local complet avant deploy
3. Bascule DNS Cloudflare
4. Télécharger TOUTES les pages avec curl -sL
5. Vérifier chaque HTML > 4000 bytes
6. Ne modifier QUE les fichiers concernés

## Réglementation

- RGPD : consentement explicite, hébergement EU, DPO à nommer
- HDS : migration OVHcloud/Scaleway en Phase 2
- CORTEX = outil bien-être, PAS dispositif médical (UE 2017/745)
- Disclaimer obligatoire dans l'app
