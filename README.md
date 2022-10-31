# 420-W48-SF-TP01 : Les BonBons Sucrés

## 1 - Directives

### 1.1 - Déroulement du TP

- Remise du travail: 21 novembre 2022, 23:59
- Ce travail est réalisé en équipe de 2 personnes et seuls les membres de cette équipe y contribuent
- Toutes les réponses fournies doivent être originales (produites par l’étudiant ou un membre de l’équipe)
- Toute copie de code, de portion de code, d’algorithme ou de texte doit faire mention de sa source
- L’emprunt ou la copie de code ou de portions de code est interdite
- Tout constat de plagiat, tricherie ou fraude sera automatiquement déclaré à la Direction et les sanctions prévues seront appliquées
- Vous devez utiliser votre dépôt Git et Teams pour faire votre travail : si une situation particulière est détectée, vos commits moduleront votre note dans le groupe et peut même aller jusqu'à un zéro en cas de non participation

## 1.2 - À remettre sur la plateforme d'enseignement Léa

- Un document Word contenant les détails du projet
- Votre code source C++ avec la structure de PlatformIO
- Vous devez fournir le lien d'une vidéo de 5 minutes illustrant le circuit, le code et le fonctionnement :
  - La vidéo doit être déposée sur YouTube
  - En lien non listé
  - La vidéo doit être accessible jusqu'à un an après la remise du travail
  - La vidéo doit être en français

En résumé, vous pouvez simplement archiver le contenu de votre dépôt Git qui devrait contenir tous ces éléments au moment de la remise.

## 1.3 - Structure de la remise

- Vous devez remplir le fichier ```AUTHORS.md```. Il donne le nom et matricule des équipiers
- Le lien de la vidéo doit indiqué dans le document word et dans le fichier ```AUTHORS.md```
- Votre code source doit être dans le répertoire  ```src``` du présent dépôt Git
- Le répertoire source doit suivre la structure d’un projet Platform.io
- Le répertoire ```doc``` doit contenir votre rapport de TP

## 2 - Description du projet

Pour la St-Valentin, notre client, ```LesBonBonsSucrés```, désire connaître l'achalandage des visiteurs qui circulent dans son commerce pour acheter des friandises. Une campagne de publicité monstre est prévue. Ces informations permettront de prévoir l'approvisionnement.

Votre tâche générale consiste à mettre en place un programme de gestion qui contrôle les va-et-vient des clients à la porte de la boutique. Vous utiliserez un bouton pour compter le nombre de clients qui entrent dans la boutique, et un autre pour le nombre de clients qui quittent la boutique. Des détecteurs de mouvement remplaceront les boutons dans la mise en place finale.

Pour attirer l'attention des passants à l'extérieur de la boutique, un ensemble de six indicateurs DELs sont installés dans la vitrine de la boutique. L'affichage des DELs représente le nombre de clients à l'intérieur de la boutique, en format binaire. Ainsi, à chaque fois que quelqu'un entre ou sort, cela crée une animation des DELs.

Le SPCI de la municipalité, ```service de protection contre les incendies```, a établi que le nombre maximal de clients présents en même temps dans la boutique ne doit pas dépasser 42 personnes. Afin d'aviser la propriétaire et les commis, un dispositif lumineux doit être prévu. Il consistera en une DEL RGB, qui passera progressivement de vert, à orange, à rouge.

Ce système comprend :

- Un "ensemble de 6 DELs" représentant le nombre de clients en boutique (il reste donc 3 DELs à votre disposition pour une implantation originale)
- Deux boutons poussoirs, actionnés au passage des clients, entrant et sortant de la boutique
- Une DEL-RGB modifiant la couleur de son éclairage selon le critères du SPCI
- Un microcontrôleur Arduino UNO et une carte de circuit électronique contenant les composants pour le bon fonctionnement du système
- Un document technique décrit plus loin

### 2.1 - Mise en place du VaEtVient

Au passage d'un client à la porte de la boutique, chaque entrée est enregistrée. De la même façon, à la sortie d'un client, sa sortie est enregistrée. Ce mouvement est illustré par un tableau d'affichage de 6 DELs dans la vitrine de la boutique, ceci en format binaire.
Lorsque le seuil de 24 personnes sont présentes, la DEL-RGB passe au orange.
Lorsque le seuil de 36 personnes sont présentes, la DEL-RGB passe au rouge.
En d'autres temps, la DEL-RGB est au vert.

### 2.2. - Analyse statistique

L'achalandage consiste en deux valeurs : nombre d'entrées et nombre de sorties, pour chaque journée. L'achalandage est gardée pour un cycle de 7 jours.

Deux raisons exigent que l'achalandage soit mémorisé :

- En cas de panne de courant, les données doivent être récupérées pour la poursuite des activités. Aussi, le SPCI et la compagine d'assurance demandent à ce que l'historique de 7 jours consécutifs soient disponibles pour consultation
- Vous devez trouver un moyen d'afficher facilement l'achalandage au démarrage du système et sur demande. Vous devez également trouver un moyen de réinitialiser le tout à 0 pour une nouvelle journée.

## 3 - Détail de l'évaluation

### 3.1 - Répartition des points

Vous devez faire le travail en équipe de 2 personnes, au maximum. Le document doit indiquer les tâches respectives que chaque personne aura fait.

1. Document de présentation du projet : (Contexte : 15%, Circuit : 20%, Coût : 5% = 40%)
   - Contexte du projet
   - Planification, attribution des tâches
   - La forme pourra être un texte explicatif ou un schéma hiérarchique des différentes étapes du projet
   - Dessiner un schéma du circuit
   - Dessiner le montage (En utilisant des images des PCB et des lignes qui représentent les fils)
   - Diagramme de classes
   - Inventaire des pièces : estimation des coûts des pièces
   - Estimation énergétique : durée de vie des batteries / consommation si sur secteur
   - Schéma technique avec explications

2. Vidéo de présentation (Présentation : 3%, Explication : 4%, Fonctionnement : 3% = 10%)
   - Projet
   - Circuit
   - Feux / boutons
   - Pièces
   - Les différents états / séquences
   - Statistiques

3. Registre des heures consacrées au projet (5%). Le registre contient la liste des activités et le temps consacré à chaque activité et identifié au participant concerné
4. Fonctionnalités : (45 %)
   1. Incrémentation / décrémentation du nombre de passants (5%)
   2. Enregistrement du nombre de passants par jour sur 7 jours (écriture cyclique) (5 + 10 = 15%)
   3. Passage à la journée suivante (5%)
   4. Animation à chaque incrémentation (5%)
   5. Affichage du nombre de personnes présentes dans le magasin (5%)
   6. Affichage simple des données au démarrage et sur demande (5 + 5 = 10%)

Durant l'évaluation de vos projets, les enseignants vont consulter l'historique de Teams (Sharepoint) et de Git. La non ou la mauvaise utilisation de ces deux outils entraîne une pénalité de 20% sur la note globale.

Pourquoi ces outils ?

- Outils similaires utilisés pour collaborer en entreprise
- Validation du travail de chaque partenaire

### 3.2 - Critères appliqués durant l'évaluation

L'évaluation du travail est effectuée par les enseignants de l'UE en se basant sur :

- L'historique de Git et de Teams/Sharepoint font office de référence pour évaluer la proportion du travail effectué par chaque équipier

- La qualité et le contenu du code source :

  - Conformité du code et des normes d'écriture utilisées dans le cours
  - Respect des bonnes pratiques (STUPID / SOLID)
  - Fonctionnalité du code
  - Facilité de lecture du code
  - Modularité
  - Modularité et utilisation adéquate de la POO
  - Modèle objet
  - Paramétrisation du code
  - Utilisation de constantes
  - Utilisation de fichiers de configuration
  - Optimisation de la mémoire
  - Bonne utilisation des contraintes matérielles
  - Bonne utilisation des bibliothèques
  - Nommage
  - Propreté et homogénéité du code
  - Initialisations / fuite mémoire
  - etc.

- La qualité et le contenu du document word :
  
  - Français
  - Schéma électrique et diagramme de classes
  - Clarté et précision des explications
  - Mise en page
  - Page de présentation
  - etc.

- La qualité et le contenu de la présentation vidéo :

  - Vidéo
  - Audio
  - Explication orale des choix de conception (Ex. "Nous avons fait une classe A et une classe B. Voici la méthode M" => 0% "Nous avons fait une classe A afin de pouvoir simplifier la gestion de E et de permettre de le remplacer par F un peu plus tard et limiter les impacts en cas de XYZ" => 100% si pertinent)
  - etc.

Tout partage de code, d'explication, de bouts de texte, etc. est considéré comme du plagiat. Pour plus de détails, consultez le site (et ses vidéos) [Sois intègre du Cégep de Sainte-Foy](http://csfoy.ca/soisintegre) ainsi que [l'article 6.1.12 de la PÉA](https://www.csfoy.ca/fileadmin/documents/notre_cegep/politiques_et_reglements/5.9_PolitiqueEvaluationApprentissages_2019.pdf)
