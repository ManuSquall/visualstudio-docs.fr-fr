---
title: 'Procédure : Rechercher une fenêtre dans la vue de Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1526ed73b1a4f5c665f6b60c3cbb7e5b0b659380
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974056"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Procédure : Rechercher une fenêtre dans la vue Fenêtres
Vous pouvez rechercher une fenêtre spécifique dans la vue de Windows à l’aide de son handle, légende, classe ou une combinaison de sa légende et de la classe en tant que critères de recherche. Vous pouvez également spécifier le sens initial de la recherche. Les champs dans la boîte de dialogue affiche les attributs de la fenêtre sélectionnée dans l’arborescence de la fenêtre.  
  
 Démarrer avec l’arborescence développée au deuxième niveau (toutes les fenêtres qui sont des enfants du bureau), afin que vous puissiez identifier au niveau du bureau de windows par leur nom de classe et le titre. Une fois que vous avez choisi une fenêtre de niveau bureau, vous pouvez développer ce niveau pour rechercher une fenêtre enfant spécifique.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Pour rechercher une fenêtre dans la vue de Windows  
  
1. Réorganisez vos fenêtres donc que Spy ++, le [Windows vue](../debugger/windows-view.md) fenêtres et cible sont visibles.  
  
2. À partir de la **recherche** menu, choisissez **rechercher une fenêtre**.  
  
    Le [boîte de dialogue de recherche de fenêtre](../debugger/window-search-dialog-box.md) s’ouvre.  
  
   > [!TIP]
   >  Pour réduire l’encombrement de l’écran, sélectionnez le **Masquer Spy ++** option. Cette option masque la fenêtre principale de Spy ++ et laisse uniquement le **recherche de fenêtre** boîte de dialogue visible en haut de vos autres applications. La fenêtre principale de Spy ++ est restaurée lorsque vous cliquez sur **OK** ou **Annuler**, ou lorsque vous supprimez le **Masquer Spy ++** option.  
  
3. Faites glisser le **outil recherche** sur la fenêtre cible. Lorsque vous faites glisser l’outil, le **recherche de fenêtre** boîte de dialogue affiche des détails sur la fenêtre sélectionnée.  
  
   - ou  
  
     Si vous connaissez le handle de la fenêtre de votre choix (par exemple, à partir du débogueur), vous pouvez la taper dans le **gérer** boîte.  
  
   - ou  
  
     Si vous connaissez la légende et/ou la classe de la fenêtre que vous souhaitez, vous pouvez les taper dans la **légende** et **classe** zones de texte, puis désactivez la **gérer** zone de texte.  
  
4. Choisissez **des** ou **vers le bas** pour la direction de la recherche initiale.  
  
5. Cliquez sur **OK**.  
  
    Si une fenêtre correspondante est trouvée, elle est mise en surbrillance dans le [Windows vue](../debugger/windows-view.md) fenêtre.