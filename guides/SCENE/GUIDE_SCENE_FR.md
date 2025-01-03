# Guide de création d’une histoire par étapes (fichiers .txt)

## 1. Principe général
- Chaque fichier `.txt` représente une scène de l’histoire.
- Les fichiers sont numérotés et reliés entre eux par des choix (ex: `0.txt`, `1.txt`, `2.txt`…).
- Le joueur progresse de fichier en fichier selon les décisions prises.

## 2. Mots-clés disponibles
Les mots-clés s’écrivent en majuscules, encadrés d’astérisques. Ils servent à définir des actions spécifiques ou des éléments de jeu.

### PATH
Propose un choix qui mène à d’autres scènes.

**Format :**
```
*PATH*
X Description du choix 1
Y Description du choix 2
```
Où `X` et `Y` sont les numéros des fichiers vers lesquels mènent les choix (ex: `1.txt`, `2.txt`).

**Exemple :**
```
*PATH*
7 Prendre à gauche.
6 Prendre à droite.
```

**Affichage**
```
1. Prendre à gauche.
2. Prendre à droite.
```

### COMBAT
Initie un combat contre un monstre.

**Format :**
```
*COMBAT*
Nom_du_Monstre
Points_de_vie
Points_d'armure
Points_d'attaque
```

**Exemple :**
```
*COMBAT*
Mimic
15
1
3
```

### ARME
Ajoute une arme à l’inventaire du joueur, augmentant son attaque.

**Format :**
```
*ARME*
Nom_de_l'Arme
Bonus_d'attaque
```

**Exemple :**
```
*ARME*
Epée Rouillée
2
```

### ARMURE
Ajoute une armure à l’inventaire du joueur, augmentant sa protection.

**Format :**
```
*ARMURE*
Nom_de_l'Armure
Bonus_de_protection
```

**Exemple :**
```
*ARMURE*
Armure Légère
3
```

### VICTOIRE
Indique la fin de l’histoire ou une victoire majeure.

**Format :**
```
*VICTOIRE*
```

### GO
Termine l’histoire abruptement (défaite, abandon, etc.).

**Format :**
```
*GO*
```

## 3. Structure recommandée d’un fichier de scène
1. **Description de la scène :** Situez le joueur (environnement, ambiance).
2. **Événements :** S’il y a un combat, placez le bloc `*COMBAT*` après la description.
3. **Récompenses :** Après le combat, si une arme ou une armure est trouvée, utilisez `*ARME*` ou `*ARMURE*`.
4. **Choix :** Proposez des options, puis `*PATH*` pour indiquer les chemins vers les autres fichiers.

## 4. Conseils de conception
- **Éviter les boucles infinies :** Chaque choix doit mener à une conclusion, un nouvel événement, ou un retour en arrière logique.
- **Cohérence des récompenses :** Les armes et armures doivent être proportionnées à la difficulté.
- **Varier les situations :** Combats, découvertes, récompenses, descriptions, pour maintenir l’intérêt du joueur.

## 5. Exemple

**Fichier 0.txt :**
```
Vous commencez dans une forêt dense. Deux sentiers s’offrent à vous.

*PATH*
1 Prendre à gauche.
2 Prendre à droite.
```

**Fichier 1.txt :**
```
Un loup se dresse devant vous, prêt à attaquer.

*COMBAT*
Loup
10
0
3

Vous vainquez le loup et trouvez une épée rouillée.

*ARME*
Epée Rouillée
2

*PATH*
3
```

**Fichier 2.txt :**
```
Vous débouchez sur une clairière ensoleillée. Au centre, une armure scintille.

*ARMURE*
Armure Légère
3

*PATH*
0 Revenir sur vos pas.
4 Avancer plus loin.
```
