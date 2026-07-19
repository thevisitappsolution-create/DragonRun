# À Vue — puzzle d'observation

Jeu web/PWA du [PRD_A_Vue.md](PRD_A_Vue.md) : une scène apparaît, tu **écris ce que tu vois**, chaque bon mot efface l'objet correspondant. Vide la scène avant la fin du chrono !

**Jouer :** https://thevisitappsolution-create.github.io/DragonRun/
Sur iPhone : Safari → Partager → **« Sur l'écran d'accueil »** → plein écran + hors-ligne (PWA).

## Modes

| Mode | Joueurs | But |
|---|---|---|
| **Campagne** | Solo | 50 niveaux générés (12 thèmes), chrono 60→40 s, étoiles ★★★ |
| **Contre-la-montre** | Solo | Max d'objets en 30/60/90 s (+3 pts par scène vidée), records sauvegardés |
| **Duel — Rapidité** | 2 (même appareil) | Même scène chacun son tour, le plus rapide gagne · 3 manches |
| **Baccalauréat** | 2 (même appareil) | Mêmes scènes, même durée, meilleur score gagne |

## Fonctionnalités

- **Saisie tolérante** : majuscules, accents et petites fautes pardonnés (distance d'édition 1–2), synonymes par objet (« canapé/sofa/divan »).
- **Zoom & pan** : pincer, glisser, double-tap, bouton 1:1.
- **Indice** 💡 : initiale d'un objet + halo, contre +3 s.
- **Génération procédurale déterministe** : 12 thèmes, 4→11 objets, sans doublons de mots.
- **Onboarding** au premier lancement, **musique** et SFX WebAudio (réglables), progression et records en localStorage.
- **PWA** : installable, hors-ligne (service worker), clavier iOS géré (visualViewport).

## Fichiers

- `index.html` — tout le jeu (HTML/CSS/JS autonome, zéro dépendance)
- `manifest.webmanifest`, `service-worker.js`, `icon-180.png`, `icon-512.png` — PWA
- `PRD_A_Vue.md` — document produit

## Réglages rapides

Dans `index.html` : `THEMES` (contenus + synonymes), `countFor`/`timeFor` (difficulté campagne), seuils d'étoiles dans `startCampaign`, tolérance dans `findMatch`.
