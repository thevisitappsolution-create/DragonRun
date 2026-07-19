# Firecoil — prototype jouable (Phase 0+)

Prototype HTML5 auto-contenu du jeu décrit dans [PRD_Firecoil.md](PRD_Firecoil.md).

**Pour jouer :** ouvrir `index.html` dans un navigateur (double-clic). Aucune installation, aucun serveur.

## Contrôles

| Action | Souris / tactile | Clavier |
|---|---|---|
| Position verticale | Glisser sur l'écran | ↑ / ↓ (ou Z/W & S) |
| Cracher du feu | Maintenir le bouton 🔥 | Maintenir **ESPACE** |
| Pause | — | P ou Échap |

Appui court = flammèche ; appui long = flamme plus longue (consomme plus, portée accrue).

## Ce que le prototype couvre (vs PRD)

- **Boucle cœur (§5–6)** : avance automatique, 3 hauteurs de cristaux, manger → grandir + accélérer + carburant ; cracher → rétrécir + ralentir. La taille du dragon reflète le carburant.
- **Feu à double usage** : la flamme fond les **murs de glace** (coût ∝ épaisseur, ils bloquent sans blesser) et brûle le **chevalier** ; la flamme se dirige vers la cible quand elle est à portée (halo orange = à portée).
- **Poursuite / minuteur** : barre de fuite en haut ; être bloqué par un mur accélère la fuite ; le chevalier trébuche parfois. Plus tu es gros/rapide, plus il est proche (donc à portée de flamme).
- **Vies & obstacles** : 3 vies, rochers / stalactites / boules hérissées / haches lancées (niveaux 2–3), reprise sur place avec invincibilité brève.
- **Combo (§6)** : enchaîner des cristaux sans dégât → flamme jusqu'à +60 %. Cristaux spéciaux dorés (+20).
- **Étoiles (§4)** : ★ cible cramée · ★★ ≥ 2 vies restantes · ★★★ zéro dégât **ou** quota de cristaux. Sauvegarde locale (localStorage).
- **3 niveaux** à difficulté croissante (PV du chevalier, murs plus épais/fréquents, plus d'obstacles, projectiles).
- **Juice (§9)** : particules, shake, slow-motion sur le kill, SFX synthétiques (WebAudio), palette chaud (dragon/feu) vs froid (glace).
- **Tutoriel progressif (§12)** : messages contextuels au niveau 1 uniquement.

## Décisions prises (parmi les points « à valider » du PRD §16)

1. **Orientation : paysage** (recommandation du PRD).
2. **Contrôle vertical : glisser-positionner libre** + flèches clavier.
3. **Une seule cible par niveau** (pas d'humains bonus pour l'instant).
4. Skins / méta / monétisation : hors scope Phase 0.

## Réglages rapides

Tout l'équilibrage est en tête du script dans `index.html` :
- `LEVELS` : PV du chevalier, temps de fuite, fréquence/épaisseur des murs, densité d'obstacles, quota 3★.
- `sizeScale`, `speedMul`, `flameMax`, `gapTarget` : l'économie taille/vitesse/feu.
