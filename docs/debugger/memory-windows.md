---
title: "Afficher la mémoire pour les Variables dans le débogueur | Documents Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 96a4dc22f4f5c96d3dd9d40a565c2656ffe6e283
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger"></a>Utiliser les fenêtres de mémoire dans le débogueur Visual Studio
Le **mémoire** fenêtre fournit une vue de l’espace mémoire utilisé par votre application. Le **espion** fenêtre, **Espion express** boîte de dialogue, **automatique** fenêtre, et **variables locales** et consulter le contenu de variables qui sont dans une fenêtre stockées à des emplacements spécifiques dans la mémoire. Mais le **mémoire** fenêtre affiche l’image à grande échelle. Cette vue peut s'avérer pratique pour l'examen de grands fragments de données (mémoires tampons ou longues chaînes, par exemple) dont l'affichage n'est pas satisfaisant dans les autres fenêtres. Toutefois, le **mémoire** fenêtre n’est pas tenu d’afficher les données. Elle affiche tout ce qui se trouve dans l'espace mémoire, qu'il s'agisse de données, de code ou de bits aléatoires de garbage de la mémoire non assignée.  
  
 Le **mémoire** fenêtre est disponible uniquement si le débogage au niveau des adresses est activé dans le **Options** boîte de dialogue, **débogage** nœud. Le **mémoire** fenêtre n’est pas disponible pour le Script ou SQL, qui sont des langages qui ne reconnaissent pas le concept de mémoire.  
  
## <a name="opening-a-memory-window"></a>Ouvrir une fenêtre Mémoire  
  
#### <a name="to-open-a-memory-window"></a>Pour ouvrir une fenêtre Mémoire  
  
1.  Démarrez le débogage, si vous n'êtes pas encore en mode débogage.  
  
2.  Dans le **déboguer** menu, pointez sur **Windows**. Ensuite, pointez sur **mémoire** puis cliquez sur **mémoire 1**, **mémoire 2**, **mémoire 3**, ou **mémoire 4**. (Les éditions de niveau inférieur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ont une seule **mémoire** fenêtre. Si vous utilisez l’une de ces éditions, cliquez simplement sur **mémoire**.)  
  
## <a name="paging-in-the-memory-window"></a>Pagination dans la fenêtre Mémoire  
 Le **mémoire** fenêtre a une barre de défilement verticale qui fonctionne de manière habituelle. L'espace adresse d'un ordinateur moderne est très important, et il serait facile de se perdre en faisant glisser le curseur de défilement vers un emplacement aléatoire. Pour cette raison, le curseur est « fixé » et reste toujours au milieu de la barre de défilement. Dans les applications en code natif, vous pouvez vous déplacer d'une page vers le haut ou vers le bas, mais il est impossible de défiler librement.  
  
 Les adresses mémoire supérieures s'affichent au bas de la fenêtre. Pour voir une adresse supérieure, faites défiler vers le bas, et non vers le haut.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Pour vous déplacer d'une page vers le haut ou vers le bas dans la mémoire  
  
1.  Pour faire défiler vers le bas (passer à une adresse mémoire supérieure), cliquez sous le curseur de la barre de défilement verticale.  
  
2.  Pour faire défiler vers le haut (passer à une adresse mémoire inférieure), cliquez au-dessus du curseur de la barre de défilement verticale.  
  
## <a name="selecting-a-memory-location"></a>Sélection d'un emplacement de mémoire  
 Si vous souhaitez déplacer instantanément vers un emplacement mémoire sélectionné, vous pouvez le faire à l’aide d’une opération de glisser-déplacer, ou en modifiant la valeur dans la **adresse** boîte. Le **adresse** zone accepte non seulement des valeurs numériques, mais aussi des expressions qui correspondent aux adresses. Par défaut, le **mémoire** fenêtre traite un **adresse** expression sous la forme d’une expression en direct, réévalue pendant l’exécution du programme. Les expressions dynamiques peuvent être très utiles. Par exemple, elles permettent d'afficher la mémoire survolée par un pointeur.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Pour sélectionner un emplacement de mémoire par glisser-déposer  
  
1.  Dans n'importe quelle fenêtre, sélectionnez une adresse mémoire ou une variable pointeur qui contient une adresse mémoire.  
  
2.  Faites glisser l’adresse ou le pointeur vers le **mémoire** fenêtre.  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Pour sélectionner un emplacement mémoire par édition  
  
1.  Dans le **mémoire** fenêtre, sélectionnez le **adresse** boîte.  
  
2.  Tapez ou collez l’adresse que vous voulez voir, puis appuyez sur **entrée**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Modification de la façon dont la fenêtre Mémoire affiche les informations  
 Vous pouvez personnaliser la façon dont le **mémoire** fenêtre affiche le contenu de la mémoire. Par défaut, le contenu de la mémoire est affiché sous forme d'entiers d'un octet au format hexadécimal, et le nombre de colonnes est automatiquement déterminé en fonction de la largeur actuelle de la fenêtre.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Pour modifier le format du contenu mémoire  
  
1.  Cliquez sur le **mémoire** fenêtre.  
  
2.  Choisissez le format souhaité.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Pour modifier le nombre de colonnes affichées dans la fenêtre Mémoire  
  
1.  Dans la barre d’outils en haut de la **mémoire** fenêtre, recherchez le **colonnes** liste.  
  
2.  Dans le **colonnes** , sélectionnez le nombre de colonnes que vous souhaitez afficher ou sélectionner **automatique** pour l’ajustement automatique à la largeur de la fenêtre.  
  
 Si vous ne souhaitez pas que le contenu de la **mémoire** fenêtre Modifier en tant que votre programme s’exécute, vous pouvez désactiver l’évaluation dynamique des expressions.  
  
#### <a name="to-toggle-live-evaluation"></a>Pour activer ou désactiver l'évaluation dynamique  
  
1.  Cliquez sur le **mémoire** fenêtre.  
  
2.  Dans le menu contextuel, cliquez sur **réévaluer automatiquement**.  
  
     Si l'évaluation dynamique est activée, l'option sera sélectionnée. Si vous cliquez sur l'option, l'évaluation dynamique sera désactivée. Si l'évaluation dynamique est désactivée, l'option ne sera pas sélectionnée. Si vous cliquez sur l'option, l'évaluation dynamique sera activée.  
  
 Vous pouvez masquer ou afficher la barre d’outils en haut de la **mémoire** fenêtre. Vous n'avez pas accès à la zone Adresse ou aux autres outils tant que la barre d'outils est masquée.  
  
#### <a name="to-toggle-the-toolbar"></a>Pour basculer la barre d'outils  
  
1.  Avec le bouton droit une **mémoire** fenêtre.  
  
2.  Dans le menu contextuel, cliquez sur **afficher la barre d’outils**.  
  
     La barre d'outils disparaît ou apparaît, selon son état précédent.  
  
## <a name="following-a-pointer-through-memory"></a>Suivi d'un pointeur dans la mémoire  
 Dans des applications en code natif, des noms de registres peuvent être utilisés comme expressions dynamiques. Par exemple, vous pouvez utiliser le pointeur de pile pour suivre la pile.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Pour suivre un pointeur dans la mémoire  
  
1.  Dans le **mémoire** fenêtre **adresse** , tapez une expression de pointeur. La variable pointeur doit se trouver dans la portée actuelle. Vous devrez la déréférencer en fonction du langage.  
  
2.  Appuyez sur **Entrée**.  
  
     Désormais, lorsque vous utilisez une commande d’exécution tels que **étape**, l’adresse mémoire affichée change automatiquement avec le pointeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)