---
title: Mode Plan | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 939bb5ac1188a54217339c1bf3e9e3a828493d90
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494062"
---
# <a name="outlining"></a>mode Plan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [mode plan](https://docs.microsoft.com/visualstudio/ide/outlining).  
  
Vous pouvez choisir de masquer certaines parties du code en réduisant une zone de code pour qu’elle apparaisse sous un signe plus (+). Pour développer une zone réduite, vous devez cliquer sur le signe plus (+). (Vous pouvez aussi appuyer sur Ctrl + M + M pour réduire une zone, puis sur Ctrl + M + M pour la redévelopper.) Vous pouvez aussi réduire une zone en mode Plan en double-cliquant sur n’importe quelle ligne dans la zone dans la marge de mode Plan, affichée juste à gauche du code. Vous pouvez afficher le contenu d’une zone réduite sous forme d’info-bulle quand vous pointez sur la partie réduite.  
  
 Les zone dans la marge de mode Plan sont également mises en surbrillance quand vous pointez sur la marge avec la souris. La couleur de mise en surbrillance par défaut peut sembler plutôt fade dans certaines configurations de couleur. Vous pouvez la modifier dans **Outils/Options/Environnement/Polices et couleurs/Zone réductible**.  
  
 Quand vous travaillez dans du code en mode Plan, vous pouvez développer les sections sur lesquelles vous souhaitez travailler, les réduire quand vous avez terminé, puis basculer vers d’autres sections. Quand vous ne souhaitez pas afficher le mode Plan, vous pouvez utiliser la commande **Arrêter le mode Plan** pour supprimer les informations de mode Plan sans endommager le code sous-jacent.  
  
 Les commandes **Annuler** et **Restaurer** du menu **Edition** affectent ces actions. Les opérations **Copier**, **Couper**, **Coller** et glisser-déplacer conservent les informations de mode Plan, mais pas l’état de la zone réductible. Par exemple, quand vous copiez une zone réduite, l’opération **Coller** colle le texte copié en tant que zone développée.  
  
> [!CAUTION]
>  Quand vous modifiez une zone en mode Plan, vous risquez de perdre le mode Plan. Par exemple, une suppression ou une opération de remplacement peut effacer la fin de la zone.  
  
 Les commandes suivantes sont disponibles dans le sous-menu **Edition/Mode Plan**.  
  
|||  
|-|-|  
|Masquer la sélection|(Ctrl + M, Ctrl + H) - Réduit un bloc de code sélectionné qui ne serait normalement pas disponible pour le mode Plan, par exemple un bloc `if`. Pour supprimer la zone personnalisée, utilisez **Arrêter le masquage actuel** (ou Ctrl + M, Ctrl + U). Non disponible en Visual Basic.|  
|Activer/Désactiver le développement du mode Plan|- Inverse l’état masqué ou développé actuel de la section en mode Plan la plus intérieure quand le curseur se trouve dans une section réduite imbriquée.|  
|Activer/Désactiver toutes les régions en mode Plan|(Ctrl + M, Ctrl + L) - Définit toutes les zones au même état réduit ou développé. Si certaines zones sont développées et d’autres réduites, les zones réduites sont développées.|  
|Arrêter le mode Plan|(Ctrl + M, Ctrl + P) - Supprime toutes les informations de mode Plan pour la totalité du document.|  
|Arrêter le masquage actuel|(Ctrl + M, Ctrl + U) - Supprime les informations de mode Plan pour la zone définie par l’utilisateur actuellement sélectionnée. Non disponible en Visual Basic.|  
|Réduire aux définitions|(Ctrl + M, Ctrl + O) - Réduit les membres de tous les types.|  
|Réduire le bloc :\<limite logique>|(Visual C++) Réduit une zone dans la fonction contenant le point d’insertion. Par exemple, si le point d’insertion se trouve à l’intérieur d’une boucle, celle-ci est masquée.|  
|Réduire tout dans : \<structures logiques>|(Visual C++) Réduit toutes les structures à l’intérieur de la fonction.|  
  
 Vous pouvez également utiliser le SDK Visual Studio pour définir les zones de texte que vous souhaitez développer ou réduire. Consultez [Procédure pas à pas : mode Plan](../extensibility/walkthrough-outlining.md).



