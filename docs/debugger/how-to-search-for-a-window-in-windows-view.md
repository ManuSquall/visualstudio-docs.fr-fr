---
title: "How to: Search for a Window in Windows View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "windows, searching in Windows view"
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Window in Windows View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez rechercher une fenêtre spécifique dans la vue Fenêtres en utilisant son handle, sa légende, sa classe ou une combinaison de sa légende et de sa classe comme critères de recherche.  Vous pouvez également spécifier la direction initiale de la recherche.  Les champs de la boîte de dialogue affichent les attributs de la fenêtre sélectionnée dans l'arborescence des fenêtres.  
  
 Commencez avec l'arborescence développée au deuxième niveau \(toutes les fenêtres enfants du Bureau\), afin de pouvoir identifier les fenêtres de niveau Bureau par leur nom de classe et leur titre.  Une fois que vous avez choisi une fenêtre de niveau Bureau, vous pouvez développer ce niveau pour rechercher une fenêtre enfant spécifique.  
  
### Pour rechercher une fenêtre dans la vue Fenêtres  
  
1.  Réorganisez vos fenêtres afin que Spy\+\+, la fenêtre [Vue Fenêtres](../debugger/windows-view.md) et la fenêtre cible soient visibles.  
  
2.  Dans le menu **Rechercher**, choisissez **Rechercher une fenêtre**.  
  
     La [boîte de dialogue Recherche d'une fenêtre](../debugger/window-search-dialog-box.md) s'ouvre.  
  
    > [!TIP]
    >  Pour réduire l'encombrement de l'écran, activez la case à cocher **Masquer Spy\+\+**.  Cette option permet de dissimuler la fenêtre principale de Spy\+\+ et de laisser uniquement la boîte de dialogue **Recherche d'une fenêtre** visible au premier plan de vos applications.  La fenêtre principale de Spy\+\+ est restaurée lorsque vous cliquez sur **OK** ou **Annuler**, ou lorsque vous désactivez la case à cocher **Masquer Spy\+\+**.  
  
3.  Faites glisser l'**outil Recherche** sur la fenêtre cible.  Lorsque vous faites glisser l'outil, la boîte de dialogue **Recherche d'une fenêtre** affiche des informations sur la fenêtre sélectionnée.  
  
     \- ou \-  
  
     Si vous connaissez le handle de la fenêtre souhaitée \(à partir du débogueur, par exemple\), vous pouvez le taper dans la zone **Handle**.  
  
     \- ou \-  
  
     Si vous connaissez le titre et\/ou la classe de la fenêtre souhaitée, vous pouvez taper les informations correspondantes dans les zones de texte **Légende** et **Classe**, et effacer le contenu de la zone de texte **Handle**.  
  
4.  Sélectionnez **Haut** ou **Bas** comme direction initiale de la recherche.  
  
5.  Cliquez sur **OK**.  
  
     Si une fenêtre correspondante est trouvée, elle est mise en surbrillance dans la fenêtre [Vue Fenêtres](../debugger/windows-view.md).