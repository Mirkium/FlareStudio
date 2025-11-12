# 🎮 Projet UE5 RPG – Guide Git & Workflow

## 🧱 Architecture des branches

main
└── dev
├── AI-Ennemie
├── Principal-/-Pause-Menu
├── Inventaire
├── Respawn-/-Dead-system
├── Border_Zone
├── Movement
└── (autres branches filles à venir)

yaml
Copy code

### 🔹 Rôle des branches
| Branche | Rôle |
|----------|------|
| **main** | Version stable et jouable du projet. Aucun push direct. |
| **dev** | Branche principale de développement. Intègre les features validées. |
| **branches filles** | 1 branche = 1 fonctionnalité ou tâche spécifique. Toutes sont créées depuis `dev`. |

---

## ⚙️ Création d’une nouvelle branche

### 🪄 Quand ?
À **chaque nouvelle fonctionnalité ou tâche**, crée une branche **fille de `dev`**.

### 🧩 Commandes :
```bash
# Se placer sur dev
git checkout dev

# Mettre à jour dev avant de créer la nouvelle branche
git pull origin dev

# Créer la branche fille
git checkout -b NomFeature

# Exemple :
git checkout -b IA-Combat
🏷️ Convention de nommage :
php-template
Copy code
<Type>-<NomFonctionnalité>
Exemples :

Player-Movement

System-Inventory

UI-MenuPause

IA-BossPattern

Fix-Respawn

🧾 Convention de commit
Chaque commit doit être clair, court et précis.
Utilise un préfixe de type pour décrire ton changement.

✅ Format :
markdown
Copy code
[type]: description courte
Types les plus utilisés :
Type	Description
feat	Nouvelle fonctionnalité
fix	Correction de bug
refactor	Réécriture/amélioration sans ajout de feature
style	Changement visuel, indentation, renommage
test	Ajout ou modification de tests
doc	Mise à jour de documentation

💡 Exemples :
vbnet
Copy code
feat: ajout du système de respawn
fix: correction du bug de collision sur la border zone
refactor: simplification du blueprint IA basique
doc: ajout du guide Git dans le readme
🔄 Workflow complet
1️⃣ Créer ta branche
bash
Copy code
git checkout dev
git pull origin dev
git checkout -b NomFeature
2️⃣ Coder et faire des commits réguliers
bash
Copy code
git add .
git commit -m "feat: ajout du menu pause"
3️⃣ Pousser ta branche sur le dépôt
bash
Copy code
git push origin NomFeature
4️⃣ Créer une Pull Request
Base : dev

Compare : ta branche

Titre : NomFeature – courte description

Assigne-toi et ajoute un reviewer (autre dev)

5️⃣ Merge vers dev
Une fois la PR validée :

Merge ta branche vers dev

Supprime la branche locale et distante :

bash
Copy code
git branch -d NomFeature
git push origin --delete NomFeature
⚠️ Bonnes pratiques
✔️ Toujours faire un git pull origin dev avant de créer une branche
✔️ Ne jamais merger directement sur main
✔️ Commits courts et fréquents
✔️ Bien nommer branches et commits
✔️ Après un merge, mettre à jour ta branche locale dev :

bash
Copy code
git checkout dev
git pull origin dev
🧩 Exemple concret
Tu dois coder la régénération de PV du joueur :

bash
Copy code
git checkout dev
git pull origin dev
git checkout -b Player-RegenPV

# Développement...
git add .
git commit -m "feat: ajout du système de régénération de PV"
git push origin Player-RegenPV
Ensuite, ouvre une Pull Request :

Base : dev
Compare : Player-RegenPV
Titre : Ajout du système de régénération de PV

🧠 Résumé rapide
Étape	Action
1️⃣	Crée une branche fille de dev
2️⃣	Code et fais des commits clairs
3️⃣	Push ta branche
4️⃣	Fais une PR vers dev
5️⃣	Merge après validation

