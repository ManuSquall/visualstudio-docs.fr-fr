---
title: "Mode Plan | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode Plan"
  - "Visual Studio, développer/réduire le code"
  - "Visual Studio, mode Plan"
  - "développer/réduire le code"
  - "code [Visual Studio], mode Plan"
  - "code [Visual Studio], masquer"
  - "code en mode Plan"
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Mode Plan
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Choisissez de masquer du code à la vue en réduisant une zone de code afin qu'il apparaisse sous un signe plus \(\+\).  Vous développez une région réduite en cliquant sur le signe plus. \(Vous pouvez également appuyer sur Ctrl \+ M \+ M pour réduire une région puis un Ctrl\+ M \+ M pour l'afficher à nouveau.\) Réduisez encore une région en mode Plan en double\-cliquant sur n'importe quelle ligne dans la zone de la marge en mode Plan, qui s'affiche juste à gauche du code.  Consultez le contenu d'une zone réduite comme info\-bulle lorsque vous placez sur la zone réduite.  
  
 Les régions dans la marge en mode Plan sont également mises en surbrillance lorsque vous placez sur la marge avec la souris.  La couleur de surbrillance par défaut peut sembler plutôt terne dans certaines configurations de couleur.  Vous pouvez la modifier dans **Outils\/options\/environnement\/polices et couleurs\/région réductible**.  
  
 Lorsque vous travaillez en mode Plan, vous pouvez développer les sections sur lesquelles vous voulez travailler, les réduire quand vous avez terminé, puis vous déplacer vers une autre section.  Si vous ne souhaitez pas que le mode Plan s'affiche, utilisez la commande **Arrêter le mode Plan** pour enlever les informations en mode Plan sans que cela n'affecte le code sous\-jacent.  
  
 Les commandes **Annuler** et **Rétablir** du menu **Edition** influent sur ces actions.  Par ailleurs, les opérations **Copier**, **Couper**, **Coller** et Glisser\-déplacer conservent les informations en mode Plan mais pas l'état de la zone réductible.  Par exemple, lorsque vous copiez une zone réduite, l'opération **Coller** collera le texte copié en tant que zone développée.  
  
> [!CAUTION]
>  Lorsque vous modifiez une zone avec contour, les informations du mode Plan peuvent être perdues.  Par exemple, les opérations de suppression ou de Recherche et remplacement peuvent effacer la fin de la zone.  
  
 Les commandes suivantes se trouvent dans le sous\-menu **Modification\/mode Plan**.  
  
|||  
|-|-|  
|Masquer la sélection|\(Ctrl \+ M, Ctrl \+ H\) \- réduit un bloc de code sélectionné qui ne serait normalement pas disponible pour le mode Plan, par exemple un bloc `if`.  Pour supprimer la zone personnalisée, utilisez **Arrêter le masquage actuel** \(ou Ctrl \+ M, Ctrl \+ U\).  Non disponible en Visual Basic.|  
|Activer\/Désactiver le développement du mode Plan|Inverse l'état en cours \(masqué ou développé\) de la section du mode Plan la plus interne lorsque le curseur se trouve dans une section réduite imbriquée.|  
|Activer\/Désactiver tout le mode Plan|\(Ctrl \+ M, Ctrl \+ L\) \- Impose le même état \(réduit ou développé\) à toutes les régions.  Si certaines zones sont développées et d'autres masquées, alors les zones masquées sont développées.|  
|Arrêter le mode Plan|\(Ctrl \+ M, Ctrl \+ P\) \- Supprime toutes les informations en mode Plan dans l'ensemble du document.|  
|Arrêter le masquage en cours|\(Ctrl \+ M, Ctrl \+ U\) \- Supprime les informations en mode Plan pour la zone sélectionnée définie par l'utilisateur.  Non disponible en Visual Basic.|  
|Réduire aux définitions|\(Ctrl \+ M, Ctrl \+ O\) \- Réduit les membres de tous les types.|  
|Réduire le bloc :\<limite logique\>|\(Visual C\+\+\) réduit une zone dans la fonction contenant le point d'insertion.  Par exemple, si le point d'insertion se trouve dans une boucle, la boucle est masquée.|  
|Réduire tout dans : \<structures logiques\>|\(Visual C\+\+\) réduit toutes les structures à l'intérieur de la fonction.|  
  
 Vous pouvez également utiliser le Kit de développement logiciel Visual Studio pour définir les zones de texte que vous voulez développer ou réduire.  Consultez [Procédure pas à pas : mise en relief](../extensibility/walkthrough-outlining.md).