# PRD — « Firecoil » (titre de travail)

*Alternatives de nom : Ember Chase · Dragon Feast · Wyrmfire · Baby Draco*

**Version :** 0.1 (draft à itérer)
**Statut :** Concept validé, en cadrage MVP
**Genre :** Casual à progression (« hybrid-casual ») · Poursuite en défilement latéral · Collecte + gestion de ressource
**Structure :** Niveaux-poursuites regroupés en mondes
**Plateformes :** iOS + Android

> Les points marqués **[à valider]** sont mes propositions par défaut. Rien n'y est figé.

---

## 1. En une phrase

Un bébé dragon-serpent (façon dragon chinois) vole en poursuivant un chevalier qui fuit vers une sortie. Il gobe des cristaux de feu pour grandir et accumuler du carburant, puis crache des flammes pour fondre les murs de glace qui le bloquent **et** cramer sa cible avant qu'elle ne s'échappe.

## 2. Le hook (pourquoi ça accroche)

Deux boucles de tension qui s'imbriquent :

- **Grandir vs dépenser.** Manger des cristaux te rend gros et rapide (tu rattrapes ta cible), mais tu es *obligé* de cracher du feu pour tuer — ce qui te fait rétrécir et ralentir. Tu ne peux pas juste thésauriser : il faut convertir.
- **Le feu à double usage.** Ce même carburant sert à fondre les murs de glace (progresser) ET à brûler le chevalier (gagner). À chaque mur de glace, un vrai dilemme : je crame le mur, ou je garde mon feu pour la cible qui gagne du terrain vers la sortie ?

C'est ce push-pull, sous pression d'un minuteur (la course du chevalier vers la sortie), qui donne la rejouabilité. Références : *Jetpack Joyride* (collecte + esquive en défilement latéral), *Snake / Slither* (grandir en mangeant), avec une couche boss-chase à minuteur.

## 3. Cible & positionnement

- **Joueurs :** casual à mid-core light, 10–40 ans, qui aiment progresser (niveaux, étoiles, upgrades) autant que le skill du moment.
- **Sessions :** 3–8 min, plusieurs par jour, avec une méta qui donne envie de revenir.
- **Positionnement business :** hybrid-casual — mix pub + IAP, rétention plus forte et LTV plus élevée que le pur hyper-casual.

## 4. Structure du jeu

- **Niveaux-poursuites.** Chaque niveau = un segment de poursuite : le dragon traque une cible qui fuit vers une **sortie**.
- **Mondes / biomes.** Les niveaux sont groupés en mondes thématiques **[à valider]** (montagnes, grottes de glace, château, ciel…), chacun apportant décor, obstacles et cristaux nouveaux. Un **boss** clôt chaque monde (un champion plus coriace).
- **Carte de progression** avec sélection de niveau et **notation en étoiles** (1–3) selon la performance.
- **Conditions de victoire :** cramer la cible avant qu'elle n'atteigne la sortie.
- **Conditions de défaite :** la cible s'échappe (atteint la sortie), **ou** plus de vies.
- **Vies :** 3 par niveau. Toucher un obstacle → −1 vie, on **reprend sur place** (brève invincibilité). 0 vie → on recommence le niveau.

### Barème d'étoiles **[à valider]**
1 étoile : cible crâmée. 2 : + rapidité / peu de dégâts. 3 : + un quota de cristaux collectés ou zéro dégât. Les étoiles alimentent la progression et les récompenses.

## 5. Boucle de jeu

1. Le dragon avance automatiquement (défilement gauche→droite) ; le joueur contrôle sa **position verticale** et le **crachat de feu**.
2. Il gobe des cristaux répartis en 3 hauteurs (haut / milieu / bas) → il grandit, accélère, remplit sa jauge de feu.
3. Des obstacles à esquiver et des **murs de glace** à fondre jalonnent le parcours.
4. En haut de l'écran, une **barre de poursuite** montre l'avancée de la cible vers la sortie = le minuteur.
5. Le joueur crache du feu au bon moment : la flamme se dirige vers la cible (haut ou bas). Assez de feu la crame → niveau gagné.
6. Cible échappée ou vies épuisées → défaite → recommencer.

## 6. Mécaniques détaillées

### Contrôles **[à valider]**
- **Position verticale :** le joueur glisse le doigt (ou maintient pour monter / relâche pour descendre) pour placer le dragon et attraper les cristaux / esquiver.
- **Feu :** un bouton dédié. Appui court = flammèche ; appui long = flamme plus longue, qui consomme plus de carburant et fait donc plus rétrécir. Le joueur dose sa dépense.

Deux entrées (positionner + cracher) : c'est ce qui donne la profondeur « casual riche » sans devenir un jeu complexe.

### Économie taille / vitesse / feu (le cœur)
| Action | Taille | Vitesse | Carburant |
|--------|--------|---------|-----------|
| Manger un cristal | ↑ | ↑ | ↑ |
| Cracher du feu | ↓ | ↓ | ↓ |

La **jauge de carburant** (cristaux stockés) est visible en permanence. La taille du dragon reflète visuellement le carburant : gros dragon = rapide mais « lourd » à dépenser, petit dragon = lent mais économe.

### Cristaux & combos **[à valider]**
- Cristaux disposés en 3 lignes ; certains bien placés (près d'obstacles) exigent des réflexes.
- **Combo meter :** enchaîner des cristaux sans prendre de dégât charge un multiplicateur → la prochaine flamme est plus grosse / plus longue.
- **Cristaux spéciaux** (rares) : super-flamme, flamme perçante (traverse plusieurs cibles / fond un mur instantanément), etc.

### Le feu à double usage
- **Murs de glace :** bloquent le passage ; il faut les fondre au feu pour continuer. Coût en carburant proportionnel à l'épaisseur.
- **Cible :** il faut lui infliger assez de feu avant la sortie. Gérer l'arbitrage mur/cible est le skill central.

### Obstacles & vies
Obstacles non-glace (rochers, pièges, projectiles du chevalier…) à esquiver. Contact → −1 vie, reprise sur place. Les murs de glace ne coûtent pas de vie mais **bloquent** (tu perds du temps/du feu).

### La poursuite (minuteur)
La barre du haut représente la distance de la cible à la sortie. Elle avance seule ; certains événements (la cible trébuche, un passage étroit) peuvent la ralentir. C'est la source de tension permanente.

## 7. Progression & difficulté

Difficulté qui monte niveau par niveau puis monde par monde :
- Cibles plus rapides et plus « résistantes » au feu.
- Plus d'obstacles, murs de glace plus épais, placements de cristaux plus exigeants.
- Nouveaux types de cristaux / obstacles introduits progressivement, jamais à froid.
- **Boss de fin de monde :** un champion qui demande de gérer feu + esquive sous forte pression.

## 8. Méta & rétention

- **Carte du monde** avec niveaux et étoiles.
- **Upgrades persistants du dragon** : capacité de carburant max, puissance/durée de flamme, vitesse de base, agilité verticale, vie supplémentaire de départ.
- **Skins / races de dragon** : cosmétiques, éventuellement à petit bonus **[à valider]**.
- **Monnaies :** or (gagné en jeu) + gemmes (premium).
- **Boucles de retour :** récompense quotidienne, défis, événements de monde limités dans le temps.

## 9. Feedback & « juice »

- Croissance/rétrécissement du dragon très lisibles et satisfaisants (ajout/retrait de segments animés) — c'est un point artistique critique.
- Flamme punchy, impact sur la cible avec particules, shake léger, ralenti sur le kill final.
- Combo bien visible ; « super-flamme » spectaculaire.
- Contraste chaud (dragon/feu) vs froid (glace) pour une lecture instantanée.

## 10. Monétisation **[à valider — profil hybrid-casual]**

- **Pub récompensée :** revive, doubler les récompenses de niveau, coffre bonus, unlock.
- **Interstitiels :** à la fin de niveaux / défaites, avec frequency cap.
- **IAP :** packs de monnaie, remove ads, skins de dragon premium, **starter pack**.
- (Plus tard) pass saisonnier léger, offres événementielles.

L'hybrid-casual s'appuie plus sur la progression et l'IAP que le pur hyper-casual : la méta doit donner de vraies raisons de dépenser.

## 11. Direction artistique & audio **[à valider]**

- **Dragon chinois** : corps serpentin long, moustaches, ornements ; un bébé qui grandit visiblement en mangeant. La croissance/décroissance doit être le plaisir visuel n°1.
- **Palette :** dragon chaud (rouge/or/orange) qui tranche sur des obstacles froids (glace bleue) et des décors de biome variés.
- **Orientation : à trancher.** La poursuite horizontale (voir la cible devant + la barre de progression) se prête bien au **paysage** ; le **portrait une-main** est possible avec une caméra plus serrée mais réduit la visibilité de la cible. Je penche pour le paysage — à confirmer.
- **Audio :** SFX de croissance / crachat / fonte de glace bien distincts + musique épique-fun orientale.

## 12. Risques & mitigations

| Risque | Impact | Mitigation |
|--------|--------|-----------|
| **Trop de systèmes** (2 entrées + économie + méta) | Onboarding raté, abandon D1 | Tutoriel progressif, une mécanique introduite à la fois |
| **Feu double-usage mal compris** (mur vs cible) | Frustration | UI claire (jauge, cible mise en avant), premiers murs très télégraphiés |
| **Équilibrage du minuteur** (trop dur/facile) | Rétention | Beaucoup de playtests, courbe de difficulté ajustable par data |
| **Croissance/rétrécissement peu satisfaisants** | Perte du hook | Prototyper le « game feel » de la taille avant tout le reste |
| **Scope hybrid-casual coûteux** | Dérive planning/budget | Vertical slice d'un seul monde d'abord, valider avant d'industrialiser |
| **Orientation mal choisie** | Refonte tardive | Trancher paysage/portrait dès le prototype |

## 13. KPIs & benchmarks (casual à progression)

- **Rétention D1 :** > 40 % · **D7 :** > 15–20 % · **D30 :** > 5–8 %.
- **Session :** ~5–8 min, plusieurs/jour · **taux de complétion** par niveau suivi de près.
- **Monétisation :** conversion IAP ~2–5 %, ARPDAU mixte pub+IAP, LTV > CPI.
- Outils : GameAnalytics + Firebase ; A/B testing des courbes de difficulté et de l'économie.

## 14. Scope & roadmap

**Phase 0 — Prototype « game feel »**
Un niveau : avancer, positionner verticalement, manger→grandir→accélérer, cracher→rétrécir→ralentir, un mur de glace, des obstacles + 3 vies, une cible + sortie + victoire/défaite. Question : *est-ce que grandir/rétrécir est fun et est-ce que l'arbitrage feu est intéressant ?*

**Phase 1 — Vertical slice (1 monde)**
8–12 niveaux + 1 boss, juice complet, combo/cristaux spéciaux, upgrades UI, carte + étoiles, tutoriel. But : valider la boucle méta et la difficulté.

**Phase 2 — Soft launch (2–3 mondes)**
Économie complète, monétisation branchée, analytics, événements simples. Soft launch géo-limité pour mesurer rétention/LTV.

**Phase 3 — Lancement mondial + live ops**
Nouveaux mondes/cibles, skins, événements récurrents, optimisation data-driven.

## 15. Stack technique **[à valider]**

- **Moteur :** Unity 2D.
- **Backend (sauvegarde, étoiles, leaderboards, événements) :** PlayFab ou Firebase / Unity Cloud.
- **Pub :** AppLovin MAX ou Unity LevelPlay · **Analytics :** GameAnalytics + Firebase.

## 16. Décisions encore ouvertes

1. Orientation : paysage (recommandé) ou portrait ?
2. Contrôle vertical : glisser-positionner libre, ou monter/descendre façon Jetpack Joyride ?
3. Une seule cible par niveau, ou une cible « boss » + des humains bonus à cramer en chemin ?
4. Les skins donnent-ils des bonus de gameplay, ou purement cosmétiques ?
5. Détail des types de cristaux et des combos.
