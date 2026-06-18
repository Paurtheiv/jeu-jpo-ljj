# 🎮 Jeu de Visite JPO — Lycée Jean Jaurès

> Expérience interactive de visite guidée pour la Journée Portes Ouvertes  
> Lycée Jean Jaurès, Argenteuil · BTS CIEL A · Janvier 2026

---

## 📋 Description

Jeu web immersif créé pour la JPO du Lycée Jean Jaurès. Les visiteurs (collégiens, lycéens, étudiants) choisissent un guide étudiant BTS CIEL, répondent à un QCM adaptatif, visitent virtuellement les labos et découvrent les projets de la filière.

Le jeu a été utilisé en conditions réelles lors de la JPO, sur tablettes et PC dans l'espace BTS CIEL.

---

## 🎮 Déroulement

1. **Écran d'accueil** — Photo de l'entrée du lycée, voix de Jean Jaurès (IA)
2. **Choix du guide** — 3 étudiants BTS CIEL : Davina, Ugo, Dema
3. **Saisie du prénom** — personnalisation de l'expérience
4. **QCM adaptatif** — 5 questions selon le statut (collégien / lycéen / étudiant)
5. **Visite virtuelle** — couloir → labo A032 → présentation des projets
6. **Présentation des projets** — Smart Gate Jaurès + 3 autres projets BTS
7. **Score de compatibilité** — calcul du profil et message final
8. **Formulaire** — sauvegarde du prénom + guide + statut (Netlify Forms)

---

## ⚙️ Technologies

| Composant | Technologie |
|-----------|-------------|
| Interface | HTML5 / JS vanilla |
| Style | CSS custom (glassmorphism, animations) |
| Typographie | Google Fonts (Rajdhani, Roboto) |
| Audio | Web Audio API — voix synchronisées par scène |
| Voix guides | Clonage vocal IA (TopMedia) — avec consentement |
| Formulaire | Netlify Forms |
| Machine à états | Objet `scenes{}` JS — ~30 scènes |
| Responsive | Breakpoints 600px / 900px |

---

## 🏗️ Architecture du code

```
index.html          # Application complète (HTML + CSS + JS)
assets/             # Médias non versionnés (RGPD)
│  ├── davina_*.jpg      # Photos guide Davina (non public)
│  ├── ugo_*.jpg         # Photos guide Ugo (non public)
│  ├── dema_*.jpg        # Photos guide Dema (non public)
│  ├── voix/             # MP3 voix IA clonées (non public)
│  └── video_projet.mp4  # Vidéo démo Smart Gate (non public)
entree_lycee.jpg    # Photo entrée lycée
projets1-4.jpg      # Visuels projets BTS CIEL
jean_jaures.jpg     # Portrait Jean Jaurès (domaine public)
```

**Machine à états JS :**
```js
const scenes = {
  'intro':             { char, text, bg, choices },
  'selection_perso':   { ... },
  'q_col_1' → 'q_col_5': { QCM collégien },
  'q_lyc_1' → 'q_lyc_5': { QCM lycéen },
  'q_etu_1' → 'q_etu_5': { QCM étudiant },
  'couloir' → 'salle':   { visite virtuelle },
  'projet_1' → 'projet_4': { projets BTS },
  'final_message':     { score + fin }
}
```

---

## 🔒 Note RGPD

Les fichiers médias personnels (photos des guides étudiants, voix IA clonées à partir de vraies voix) **ne sont pas inclus dans ce dépôt public** conformément au RGPD. Les étudiants guides ont donné leur consentement pour l'utilisation lors de la JPO.

---

## 🎓 Contexte

Projet réalisé en autonomie dans le cadre de l'**Atelier JPO BTS CIEL**, avec participation des étudiants Davina, Ugo et Dema comme guides virtuels.

---

## 👤 Auteur

**Paurtheiv Krishna Laxman** — BTS CIEL A, Lycée Jean Jaurès, Argenteuil (95)  
📧 paurtheiv.laxman.fr@gmail.com | 🔗 [Portfolio](https://paurtheiv.github.io)
