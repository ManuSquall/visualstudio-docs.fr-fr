---
title: "Prise en main de PTVS&#160;: Interactive Python | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa594314-bdd0-4da5-874a-57b03414b675
caps.latest.revision: 4
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
caps.handback.revision: 4
---
# Prise en main de PTVS&#160;: Interactive Python
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les invites interactives ou REPL \(read\-eval\-print loop\) constituent un outil essentiel des langages de programmation productifs.  Elles vous permettent d'exécuter des extraits de code pour découvrir et apprendre des API, tester l'utilisation d'API et développer interactivement du code opérationnel à inclure dans des projets ou des programmes.  
  
 Vous pouvez voir ces instructions dans une très courte [vidéo youtube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 La fenêtre des environnements Python répertorie l'ensemble de vos environnements Python.  Sélectionnez l'un d'entre eux pour ouvrir une fenêtre interactive ou une boucle REPL.  Si vous avez déjà exécuté Python.exe à une invite de commandes, vous avez déjà vu une boucle REPL Python.  La boucle REPL se présente sous forme d'une invite, et vous pouvez entrer du code, appuyer sur Entrée et voir immédiatement les résultats de votre code.  Il s'agit d'un contexte d'exécution en direct qui inclut tous les états de vos exécutions, attributions de variables, etc.  Vous pouvez faire référence à des variables contenant des résultats lors de soumissions ultérieures à l'invite REPL.  Vous pouvez écrire plusieurs lignes de code et les exécuter toutes en même temps \(par exemple, une déclaration de méthode ou plusieurs instructions\).  
  
 Si vous vous apprêtez à utiliser une nouvelle bibliothèque, la boucle REPL est un excellent moyen de la tester.  Vous pouvez importer la bibliothèque et inspecter les sous\-packages, classes et fonctions.  Pour obtenir toutes ces informations, utilisez la fonction `help()` de Python.  Python Tools for Visual Studio \(PTVS\) vous donne également des suggestions et des informations basées sur la modélisation de code utilisée dans l'éditeur, et ce sans même exécuter la bibliothèque.  Quand vous exécutez du code, PTVS utilise les informations du runtime Python pour améliorer les suggestions fournies par PTVS.  
  
 Utile dans le cadre du développement de code itératif ou évolutionnaire, la fenêtre interactive vous permet notamment de tester votre code à mesure que vous le développez.  Vous pouvez sélectionner une fonction dans une fenêtre d'éditeur, appuyer sur le bouton droit du pointeur, puis cliquer sur Envoyer vers Interactive.  Cette commande copie la sélection dans la fenêtre interactive en tant qu'entrée suivante et l'exécute.  Vos résultats apparaissent immédiatement.  Pour apporter des modifications à l'entrée précédente, appuyez sur la flèche pour récupérer le code, modifiez\-le, puis appuyez sur Ctrl\+Entrée pour l'exécuter.  Appuyez sur Entrée à la fin d'une entrée pour l'exécuter, ou appuyez sur Entrée au milieu d'une entrée pour insérer une nouvelle ligne.  
  
 Vous pouvez ouvrir une fenêtre interactive pour chaque installation de Python, autant de fois que vous le souhaitez.  La partie supérieure de la fenêtre comprend des boutons vous permettant d'effacer l'affichage, de réinitialiser le contexte d'exécution, etc.  Votre historique reste intact.  
  
 Vous pouvez voir ces instructions dans une très courte [vidéo youtube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## Voir aussi  
 [Documentation Wiki](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [Vidéos de prise en main et de présentation approfondie de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)