---
title: "Fen&#234;tres M&#233;moire | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.memory"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Mémoire (fenêtre)"
  - "chaînes (Visual Studio), affichage"
  - "débogueur (Visual Studio), fenêtre Mémoire"
  - "mémoire (Visual Studio), débogage"
  - "débogage (Visual Studio), fenêtre Mémoire"
  - "mémoires tampons, affichage"
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fen&#234;tres M&#233;moire
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La fenêtre **Mémoire** donne un aperçu de l'espace mémoire utilisé par votre application.  Les fenêtres **Espion**, **Espion express**, **Automatique** et **Variables locales** permettent de consulter le contenu des variables, lesquelles sont stockées à des emplacements spécifiques de la mémoire,  mais la fenêtre **Mémoire** vous donne une vision d'ensemble.  Cette vue peut s'avérer pratique pour l'examen de grands fragments de données \(mémoires tampons ou longues chaînes, par exemple\) dont l'affichage n'est pas satisfaisant dans les autres fenêtres.  Toutefois, la fenêtre **Mémoire** ne se limite pas à l'affichage de données.  Elle affiche tout ce qui se trouve dans l'espace mémoire, qu'il s'agisse de données, de code ou de bits aléatoires de garbage de la mémoire non assignée.  
  
 La fenêtre **Mémoire** est disponible uniquement si le débogage au niveau des adresses est activé dans la boîte de dialogue **Options**, sous le nœud **Débogage**.  La fenêtre **Mémoire** n'est pas disponible pour les langages script et SQL qui ne reconnaissent pas le concept de mémoire.  
  
## Ouvrir une fenêtre Mémoire  
  
#### Pour ouvrir une fenêtre Mémoire  
  
1.  Démarrez le débogage, si vous n'êtes pas encore en mode débogage.  
  
2.  Dans le menu **Déboguer**, pointez sur **Fenêtres**.  Ensuite, pointez sur **Mémoire**, puis cliquez sur **Mémoire 1**, **Mémoire 2**, **Mémoire 3** ou **Mémoire 4** \(les éditions de niveau inférieur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ont une seule fenêtre **Mémoire**.  Si vous utilisez l'une de ces éditions, cliquez sur **Mémoire**\).  
  
## Pagination dans la fenêtre Mémoire  
 La fenêtre **Mémoire** dispose d'une barre de défilement verticale qui fonctionne d'une façon non conventionnelle.  L'espace adresse d'un ordinateur moderne est très important, et il serait facile de se perdre en faisant glisser le curseur de défilement vers un emplacement aléatoire.  Pour cette raison, le curseur est « fixé » et reste toujours au milieu de la barre de défilement.  Dans les applications en code natif, vous pouvez vous déplacer d'une page vers le haut ou vers le bas, mais il est impossible de défiler librement.  
  
 Les adresses mémoire supérieures s'affichent au bas de la fenêtre.  Pour voir une adresse supérieure, faites défiler vers le bas, et non vers le haut.  
  
#### Pour vous déplacer d'une page vers le haut ou vers le bas dans la mémoire  
  
1.  Pour faire défiler vers le bas \(passer à une adresse mémoire supérieure\), cliquez sous le curseur de la barre de défilement verticale.  
  
2.  Pour faire défiler vers le haut \(passer à une adresse mémoire inférieure\), cliquez au\-dessus du curseur de la barre de défilement verticale.  
  
## Sélection d'un emplacement de mémoire  
 Pour vous déplacer instantanément vers un emplacement mémoire sélectionné, utilisez le glisser\-déplacer ou modifiez la valeur dans la zone **Adresse**.  La zone **Adresse** accepte non seulement des valeurs numériques, mais aussi des expressions qui correspondent à des adresses.  Par défaut, la fenêtre **Mémoire** traite une expression **Adresse** dynamiquement et la réévalue pendant l'exécution du programme.  Les expressions dynamiques peuvent être très utiles.  Par exemple, elles permettent d'afficher la mémoire survolée par un pointeur.  
  
#### Pour sélectionner un emplacement de mémoire par glisser\-déplacer  
  
1.  Dans n'importe quelle fenêtre, sélectionnez une adresse mémoire ou une variable pointeur qui contient une adresse mémoire.  
  
2.  Glissez\-déplacez l'adresse ou le pointeur dans la fenêtre **Mémoire**.  
  
#### Pour sélectionner un emplacement mémoire par édition  
  
1.  Dans la fenêtre **Mémoire**, sélectionnez la zone **Adresse**.  
  
2.  Tapez ou collez l'adresse, puis appuyez sur **ENTRÉE**.  
  
## Modification de la façon dont la fenêtre Mémoire affiche les informations  
 Vous pouvez personnaliser la façon dont la fenêtre **Mémoire** affiche le contenu de la mémoire.  Par défaut, le contenu de la mémoire est affiché sous forme d'entiers d'un octet au format hexadécimal, et le nombre de colonnes est automatiquement déterminé en fonction de la largeur actuelle de la fenêtre.  
  
#### Pour modifier le format du contenu mémoire  
  
1.  Cliquez avec le bouton droit dans la fenêtre **Mémoire**.  
  
2.  Choisissez le format souhaité.  
  
#### Pour modifier le nombre de colonnes affichées dans la fenêtre Mémoire  
  
1.  \`Dans la barre d'outils en haut de la fenêtre **Mémoire**, localisez la liste **Colonnes**.  
  
2.  Dans la liste **Colonnes**, sélectionnez le nombre de colonnes à afficher, ou bien sélectionnez **Automatique** pour que ce nombre s'adapte automatiquement à la largeur de la fenêtre.  
  
 Pour que le contenu de la fenêtre **Mémoire** ne change pas pendant l'exécution de votre programme, vous pouvez désactiver l'évaluation dynamique des expressions.  
  
#### Pour activer ou désactiver l'évaluation dynamique  
  
1.  Cliquez avec le bouton droit dans la fenêtre **Mémoire**.  
  
2.  Dans le menu contextuel, cliquez sur **Réévaluer automatiquement**.  
  
     Si l'évaluation dynamique est activée, l'option sera sélectionnée. Si vous cliquez sur l'option, l'évaluation dynamique sera désactivée.  Si l'évaluation dynamique est désactivée, l'option ne sera pas sélectionnée. Si vous cliquez sur l'option, l'évaluation dynamique sera activée.  
  
 Vous pouvez masquer ou afficher la barre d'outils en haut de la fenêtre **Mémoire**.  Vous n'avez pas accès à la zone Adresse ou aux autres outils tant que la barre d'outils est masquée.  
  
#### Pour basculer la barre d'outils  
  
1.  Cliquez avec le bouton droit dans une fenêtre **Mémoire**.  
  
2.  Dans le menu contextuel, cliquez sur **Afficher la barre d'outils**.  
  
     La barre d'outils disparaît ou apparaît, selon son état précédent.  
  
## Suivi d'un pointeur dans la mémoire  
 Dans des applications en code natif, des noms de registres peuvent être utilisés comme expressions dynamiques.  Par exemple, vous pouvez utiliser le pointeur de pile pour suivre la pile.  
  
#### Pour suivre un pointeur dans la mémoire  
  
1.  Dans la zone **Adresse** de la fenêtre **Mémoire**, saisissez une expression de pointeur.  La variable pointeur doit se trouver dans la portée actuelle.  Vous devrez la déréférencer en fonction du langage.  
  
2.  Appuyez sur **ENTRÉE**.  
  
     Maintenant, quand vous utilisez une commande d'exécution, telle que **Pas à pas**, l'adresse mémoire affichée change automatiquement avec le pointeur.  
  
## Voir aussi  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)