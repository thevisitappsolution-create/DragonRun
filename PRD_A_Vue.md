# PRD — « À Vue »

**Version :** 1.1 — jeu jouable livré (prototype fonctionnel inclus)
**Genre :** Puzzle d'observation chronométré · casual
**Structure :** Scènes (niveaux) · solo + 2 joueurs local · modes au temps
**Plateformes :** Web / PWA (iOS, Android, desktop) — installable sur l'écran d'accueil

> Doc « as-built » : ce qui est marqué **[livré]** est déjà codé et testable. **[à valider]** = proposition par défaut. **[à décider]** = fork ouvert qui attend ton choix.

---

## 1. En une phrase

Une scène illustrée apparaît, composée de plusieurs objets. Le joueur écrit ce qu'il voit ; chaque bon mot fait disparaître l'objet correspondant, comme un calque qu'on éteint. Vider la scène le plus vite possible (ou marquer un max de points en temps limité) fait gagner.

## 2. Le hook

La satisfaction du **« ça s'efface »** : nommer juste = un objet qui disparaît dans une petite explosion, la scène qui se vide sous les yeux. C'est lisible en 3 secondes, ça se joue en rafale, et le chrono transforme une image calme en course d'observation. Le multijoueur en fait un jeu de canapé (« qui vide la scène le plus vite ? », « qui marque le plus de points ? »).

## 3. Cible & plateformes

- **Joueurs :** très large, familial (enfants qui enrichissent leur vocabulaire → adultes en défi de vitesse).
- **Plateforme :** web / PWA — un seul fichier, installable, jouable hors-ligne. Zéro friction de test, pas d'app store requis.
- **Sessions :** 1–5 min, très rejouable ; les modes au temps poussent au « encore une ».

## 4. Modes de jeu **[livré]**

| Mode | Joueurs | But | Réglages |
|------|---------|-----|----------|
| **Aventure** | Solo | Enchaîner les scènes, battre son meilleur temps | — |
| **Contre-la-montre** | Solo | Un max d'objets avant la fin du temps (+3 pts par scène vidée) | 30 / 60 / 90 s |
| **Rapidité — même carte** | 2 (même appareil) | Chacun son tour sur la même scène ; le plus rapide gagne la manche | 3 manches |
| **Baccalauréat — au temps** | 2 (même appareil) | Chacun son tour, mêmes scènes, un max de points ; meilleur score gagne | 30 / 60 / 90 s |

## 5. Boucle de jeu

1. Une scène s'affiche (objets qui apparaissent en cascade). Le chrono démarre.
2. Le joueur écrit un mot → s'il correspond à un objet, l'objet s'efface (effet + étiquette) ; sinon, feedback et on réessaie.
3. En mode chrono, chaque objet = +1 point, une scène entièrement vidée = +3 et on enchaîne la suivante.
4. Fin de scène (ou du temps) → résultat → suite / résultat de manche.

## 6. Mécaniques implémentées **[livré]**

- **Scènes en calques vectoriels.** Chaque scène est un dessin SVG où chaque objet nommable est un groupe étiqueté (`data-words`). Le fond (murs, ciel, sol) n'est pas à nommer.
- **Saisie tolérante à l'orthographe.** Insensible aux **majuscules** et aux **accents** (« éléphant » = « elephant »), et tolérante aux **fautes de frappe** (distance d'édition : « chaize » → chaise, « tabl » → table), avec **synonymes** par objet (« chaise/siège », « bateau/voilier/navire »…). Reste assez stricte pour éviter les faux positifs (« chien » ne déclenche pas « chat »).
- **Zoom & déplacement.** Pince à deux doigts pour agrandir, glisser pour se déplacer, double-tap pour zoomer/dézoomer, bouton « 1:1 » pour réinitialiser — indispensable puisque l'image est petite sur mobile.
- **Chrono** au dixième (modes libres) ou **compte à rebours** (modes au temps), avec alerte visuelle sous 5 s.
- **Indice** facultatif : met en évidence un objet restant et révèle son initiale, contre **+3 s** de malus.
- **Feedback** clair : ✓ vert sur bon mot, secousse rouge sur mauvais mot ; animation de disparition (l'objet se rétrécit et éclate en particules, l'étiquette du mot s'envole).
- **5 scènes** livrées, difficulté croissante : Le salon → La plage → Le goûter → Jardin de nuit → Dans l'espace (**34 objets** au total).

## 7. Multijoueur — état actuel et vision

### 7.1 Livré : 2 joueurs sur le même appareil **[livré]**
« Chacun son tour » (pass-and-play). Le mode **Baccalauréat** reprend l'esprit « même carte, on compte les points » : les deux joueurs affrontent les mêmes scènes avec la même durée, l'un après l'autre, et le meilleur score l'emporte.

### 7.2 À décider : simultané, chacun son téléphone **[à décider]**
Le mode « tout le monde voit la même carte, chacun joue de son côté en même temps, et dès qu'un joueur termine ça stoppe pour tout le monde » suppose une **synchronisation temps réel entre appareils** — impossible avec une simple page statique. Deux voies :

- **Pair-à-pair (WebRTC / PeerJS) avec code de partie.** Un joueur héberge, les autres rejoignent via un code ; synchronisation sans serveur à maintenir (broker de signalisation gratuit). Léger, proche de l'hébergement actuel ; dépendance externe.
- **Back-end temps réel (Firebase / Supabase, offre gratuite).** Salles, présence, scores gérés côté serveur ; plus robuste et extensible (classements, invitations), mais nécessite un compte et une clé de config.

Recommandation : commencer en **P2P** pour un premier prototype rapide, migrer vers un back-end si le mode prend et qu'on veut des classements en ligne.

## 8. Contenu & pipeline de niveaux

- **Aujourd'hui :** scènes dessinées à la main en SVG. Ajouter une scène = une entrée dans `LEVELS` avec ses objets étiquetés. Extension simple.
- **Vision « générer une image à partir de mots » :**
  1. **Composition depuis une banque d'assets** : un moteur assemble une scène à partir d'une liste de mots en piochant dans une bibliothèque d'objets vectoriels (rapide, contrôlé, garde le mécanisme de calques intact).
  2. **Génération IA + segmentation** : image générée par IA puis découpée en objets nommables (spectaculaire, mais nécessite un back-end, de la détection d'objets et un contrôle qualité — post-v1).

## 9. Progression & difficulté

Leviers : nombre d'objets par scène, objets moins évidents ou partiellement cachés (le zoom devient utile), synonymes plus rares, densité, et les modes au temps qui récompensent la vitesse. Pistes futures : niveaux « experts », scènes cachant des pièges (objets proches visuellement).

## 10. Direction artistique & audio

- **Identité :** interface sombre ardoise, accent **jaune marigold** + **turquoise** de révélation ; scènes en illustration plate « papier découpé », chaleureuses et lisibles. Typo display géométrique (Avenir) pour la personnalité, sans dépendance externe.
- **Signature :** l'animation de disparition (rétrécissement + éclat de particules + étiquette qui s'envole).
- **À ajouter [à valider] :** SFX (pop, erreur, victoire, tic-tac de fin de temps) + musique légère ; micro-animations d'ambiance par scène.

## 11. Accessibilité & UX mobile **[livré]**

- **PWA installable** (manifeste + icônes + service worker) → plein écran, hors-ligne.
- **Clavier iOS géré** : l'écran se redimensionne au viewport visible pour que le champ reste au-dessus du clavier.
- **Zoom/pan** pour les petits écrans ; cibles tactiles larges ; champ sans autocorrection ; `prefers-reduced-motion` respecté.

## 12. Monétisation **[à valider]**

Profil casual, si publication :
- Pub interstitielle légère entre parties, pub récompensée pour indices bonus.
- IAP : remove ads, packs de scènes thématiques (animaux, ville, saisons…).
- Piste premium : version sans pub, ou pack éducatif multi-langues (apprentissage du vocabulaire).

## 13. Risques & mitigations

| Risque | Impact | Mitigation |
|--------|--------|-----------|
| Objet nommé avec un mot non prévu | Frustration | Synonymes généreux + tolérance orthographe + indice ; enrichir via retours |
| Vocal (« dire ») attendu mais peu fiable sur Safari iOS | Attente déçue | Saisie clavier ; vocal en option future là où c'est supporté |
| « Image générée par IA » pris au pied de la lettre | Écart d'attente | v1 en scènes composées ; voies IA cadrées (§8) |
| Contenu limité (5 scènes) | Rétention courte | Pipeline d'ajout simple ; viser 20–30 scènes + packs |
| Mode simultané multi-appareils sous-estimé | Dérive technique | Choix P2P vs back-end tranché d'abord (§7.2), prototype avant d'industrialiser |
| Tolérance orthographe trop laxiste | Faux positifs | Seuils calibrés (distance 1 pour mots courts, 2 sinon) + tests ; ajustable |

## 14. KPIs (si publication)

Rétention D1/D7, parties par session, temps moyen par scène (équilibrage), usage des indices, taux d'installation PWA, et en multijoueur : nombre de matchs enchaînés, taux de complétion des manches.

## 15. Roadmap

- **v1.0 (livrée) :** 5 scènes, Aventure + Rapidité 2 joueurs, chrono, indices, PWA.
- **v1.1 (livrée) :** tolérance orthographe, zoom/pan, Contre-la-montre 30/60/90, Baccalauréat 2 joueurs.
- **v2 [à décider] :** multijoueur simultané multi-appareils (P2P ou back-end), SFX + musique, 20–30 scènes + packs.
- **v3 :** meilleurs temps sauvegardés, classements en ligne, moteur de composition par liste de mots (§8.1), multi-langues.
- **v4 (ambition) :** génération de scènes par IA + segmentation (§8.2).

## 16. Technique

- 100 % client, un seul `index.html` autonome (HTML/CSS/JS + SVG inline), sans dépendance ni CDN → hors-ligne, portable, hébergeable partout.
- PWA : `manifest.webmanifest` + `service-worker.js` + icônes.
- Hébergement de test : **GitHub Pages** (dépôt git prêt à pousser fourni).
- Multijoueur simultané (à venir) : dépendance réseau à choisir (§7.2).

## 17. Décisions encore ouvertes

1. **Multijoueur simultané :** P2P (WebRTC/PeerJS) ou back-end (Firebase/Supabase) — ou on s'en tient au Baccalauréat même-appareil ? *(fork prioritaire)*
2. Tolérance orthographe : garder le niveau actuel, plus stricte, ou plus souple ?
3. Ajout du son + musique avant, ou plus de scènes avant ?
4. Orientation : tout portrait, ou certaines scènes en paysage ?
5. Sauvegarde des meilleurs temps / scores (localStorage sur l'hébergement réel) ?
6. Multi-langues (fort potentiel éducatif) ?

---
## Mise à jour v1.2 — Campagne
- Mode principal = **campagne de 50 niveaux générés** (12 thèmes emoji), chaque niveau **chronométré, plafond 60 s**. [livré]
- Progression sauvegardée (déblocage + étoiles ★/★★/★★★ selon le temps restant). [livré]
- Écran de sélection des niveaux ; échec = « temps écoulé » → réessayer. [livré]
- Duel 2 joueurs conservé (3 manches sur scènes générées, le plus rapide gagne). [livré]
- Génération procédurale déterministe : difficulté croissante (4 → 11 objets), temps décroissant (60 → 40 s). [livré]
