---
title: Mode Plan | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 907d075f597799edd582c9f2bae693eac92c0b2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544961"
---
# <a name="outlining"></a>mode Plan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez choisir de masquer certaines parties du code en réduisant une zone de code pour qu’elle apparaisse sous un signe plus (+). Pour développer une zone réduite, vous devez cliquer sur le signe plus (+). (Vous pouvez aussi appuyer sur CTRL + M + M pour réduire une zone, puis sur CTRL + M + M pour la redévelopper.) Vous pouvez également réduire une région en mode plan en double-cliquant sur n’importe quelle ligne de la région dans la marge en mode plan, qui s’affiche juste à gauche du code. Vous pouvez afficher le contenu d’une zone réduite sous forme d’info-bulle quand vous pointez sur la partie réduite.

 Les zone dans la marge de mode Plan sont également mises en surbrillance quand vous pointez sur la marge avec la souris. La couleur de mise en surbrillance par défaut peut sembler plutôt fade dans certaines configurations de couleur. Vous pouvez la modifier dans **Outils/Options/Environnement/Polices et couleurs/Zone réductible**.

 Quand vous travaillez dans du code en mode Plan, vous pouvez développer les sections sur lesquelles vous souhaitez travailler, les réduire quand vous avez terminé, puis basculer vers d’autres sections. Quand vous ne souhaitez pas afficher le mode Plan, vous pouvez utiliser la commande **Arrêter le mode Plan** pour supprimer les informations de mode Plan sans endommager le code sous-jacent.

 Les commandes **Annuler** et **Restaurer** du menu **Edition** affectent ces actions. Les opérations **Copier**, **Couper**, **Coller** et glisser-déplacer conservent les informations de mode Plan, mais pas l’état de la zone réductible. Par exemple, quand vous copiez une zone réduite, l’opération **Coller** colle le texte copié en tant que zone développée.

> [!CAUTION]
> Quand vous modifiez une zone en mode Plan, vous risquez de perdre le mode Plan. Par exemple, une suppression ou une opération de remplacement peut effacer la fin de la zone.

 Les commandes suivantes sont disponibles dans le sous-menu **Edition/Mode Plan**.

|Commande|Description|
|-|-|
|Masquer la sélection|(Ctrl + M, Ctrl + H) - Réduit un bloc de code sélectionné qui ne serait normalement pas disponible pour le mode Plan, par exemple un bloc `if`. Pour supprimer la zone personnalisée, utilisez **Arrêter le masquage actuel** (ou Ctrl + M, Ctrl + U). Non disponible en Visual Basic.|
|Activer/Désactiver le développement du mode Plan|- Inverse l’état masqué ou développé actuel de la section en mode Plan la plus intérieure quand le curseur se trouve dans une section réduite imbriquée.|
|Activer/Désactiver toutes les régions en mode Plan|(Ctrl + M, Ctrl + L) - Définit toutes les zones au même état réduit ou développé. Si certaines zones sont développées et d’autres réduites, les zones réduites sont développées.|
|Arrêter le mode Plan|(Ctrl + M, Ctrl + P) - Supprime toutes les informations de mode Plan pour la totalité du document.|
|Arrêter le masquage actuel|(Ctrl + M, Ctrl + U) - Supprime les informations de mode Plan pour la zone définie par l’utilisateur actuellement sélectionnée. Non disponible en Visual Basic.|
|Réduire aux définitions|(Ctrl + M, Ctrl + O) - Réduit les membres de tous les types.|
|Réduire le bloc :\<logical boundary>|(Visual C++) Réduit une zone dans la fonction contenant le point d’insertion. Par exemple, si le point d’insertion se trouve à l’intérieur d’une boucle, celle-ci est masquée.|
|Réduire tout dans : \<logical structures>|(Visual C++) Réduit toutes les structures à l’intérieur de la fonction.|

 Vous pouvez également utiliser le SDK Visual Studio pour définir les zones de texte que vous souhaitez développer ou réduire. Consultez [Procédure pas à pas : mode Plan](../extensibility/walkthrough-outlining.md).
