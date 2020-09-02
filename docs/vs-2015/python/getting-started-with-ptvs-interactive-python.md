---
title: 'Bien démarrer avec PTVS : Interactive Python | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: fa594314-bdd0-4da5-874a-57b03414b675
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 4fba8bf658a50a7a7e28abace1eb622ab14f5f26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62550985"
---
# <a name="getting-started-with-ptvs-interactive-python"></a>Prise en main de PTVS : Interactive Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les invites interactives ou REPL (read-eval-print loop) constituent un outil essentiel des langages de programmation productifs.  Elles vous permettent d'exécuter des extraits de code pour découvrir et apprendre des API, tester l'utilisation d'API et développer interactivement du code opérationnel à inclure dans des projets ou des programmes.  
  
 Vous pouvez obtenir des instructions en regardant cette très courte [vidéo youtube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 La fenêtre des environnements Python répertorie l'ensemble de vos environnements Python.  Sélectionnez l'un d'entre eux pour ouvrir une fenêtre interactive ou une boucle REPL.  Si vous avez déjà exécuté Python.exe à une invite de commandes, vous avez déjà vu une boucle REPL Python.  La boucle REPL se présente sous forme d'une invite, et vous pouvez entrer du code, appuyer sur Entrée et voir immédiatement les résultats de votre code.  Il s’agit d’un contexte d’exécution en direct qui comprend tous les États de toutes vos exécutions, affectations de variables, etc.  Vous pouvez faire référence à des variables contenant les résultats dans les soumissions ultérieures à l’invite REPL.  Vous pouvez écrire plusieurs lignes de code et les exécuter toutes en même temps (par exemple, une déclaration de méthode ou plusieurs instructions).  
  
 Si vous vous apprêtez à utiliser une nouvelle bibliothèque, la boucle REPL est un excellent moyen de la tester.  Vous pouvez importer la bibliothèque et inspecter les sous-packages, classes et fonctions.  Pour obtenir toutes ces informations, utilisez la fonction `help()` de Python.  Python Tools for Visual Studio (PTVS) vous donne également des suggestions et des informations basées sur la modélisation de code utilisée dans l'éditeur, et ce sans même exécuter la bibliothèque.  Quand vous exécutez du code, PTVS utilise les informations du runtime Python pour améliorer les suggestions fournies par PTVS.  
  
 Utile dans le cadre du développement de code itératif ou évolutionnaire, la fenêtre interactive vous permet notamment de tester votre code à mesure que vous le développez.  Vous pouvez sélectionner une fonction dans une fenêtre d'éditeur, appuyer sur le bouton droit du pointeur, puis cliquer sur Envoyer vers Interactive.  Cette commande copie la sélection dans la fenêtre interactive en tant qu'entrée suivante et l'exécute.  Vos résultats apparaissent immédiatement.  Pour apporter des modifications à l'entrée précédente, appuyez sur la flèche pour récupérer le code, modifiez-le, puis appuyez sur Ctrl+Entrée pour l'exécuter.  Appuyez sur Entrée à la fin d'une entrée pour l'exécuter, ou appuyez sur Entrée au milieu d'une entrée pour insérer une nouvelle ligne.  
  
 Vous pouvez ouvrir une fenêtre interactive pour chaque installation de Python, autant de fois que vous le souhaitez.  Les boutons situés en haut de la fenêtre permettent de supprimer l’affichage, de réinitialiser le contexte d’exécution, etc.  Votre historique reste intact.  
  
 Vous pouvez obtenir des instructions en regardant cette très courte [vidéo youtube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation wiki](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [Vidéos sur le démarrage et l’exploration de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
