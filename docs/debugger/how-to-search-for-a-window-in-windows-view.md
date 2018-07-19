---
title: 'Comment : rechercher une fenêtre dans la vue fenêtres | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4333a79e76358216ce87697975dcb54173570534
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473434"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Comment : rechercher une fenêtre dans la vue Fenêtres
Vous pouvez rechercher une fenêtre spécifique dans la vue fenêtres à l’aide de son handle, légende, classe ou une combinaison de sa légende et de la classe comme critère de recherche. Vous pouvez également spécifier la direction initiale de la recherche. Les champs dans la boîte de dialogue affiche les attributs de la fenêtre sélectionnée dans l’arborescence de la fenêtre.  
  
 Commencez avec l’arborescence développée au deuxième niveau (toutes les fenêtres enfants du bureau), afin que vous puissiez identifier les fenêtres de niveau bureau par leur nom de classe et leur titre. Une fois que vous avez choisi une fenêtre de niveau bureau, vous pouvez développer ce niveau pour rechercher une fenêtre enfant spécifique.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Pour rechercher une fenêtre dans la vue fenêtres  
  
1.  Fenêtres ainsi que Spy ++, la [affichage Windows](../debugger/windows-view.md) fenêtre et la fenêtre cible sont visibles.  
  
2.  À partir de la **recherche** menu, choisissez **rechercher une fenêtre**.  
  
     Le [boîte de dialogue de recherche de fenêtre](../debugger/window-search-dialog-box.md) s’ouvre.  
  
    > [!TIP]
    >  Pour réduire l’encombrement de l’écran, sélectionnez le **Masquer Spy ++** option. Cette option masque la fenêtre principale de Spy ++ et laisse uniquement le **recherche de fenêtre** boîte de dialogue visible au-dessus de vos autres applications. La fenêtre principale Spy ++ est restaurée lorsque vous cliquez sur **OK** ou **Annuler**, ou lorsque vous désactivez le **Masquer Spy ++** option.  
  
3.  Faites glisser le **outil recherche** sur la fenêtre cible. Lorsque vous faites glisser l’outil, le **recherche de fenêtre** boîte de dialogue affiche des informations sur la fenêtre sélectionnée.  
  
     - ou  
  
     Si vous connaissez le handle de la fenêtre de votre choix (par exemple, à partir du débogueur), vous pouvez la taper dans le **gérer** boîte.  
  
     - ou  
  
     Si vous connaissez le titre et/ou la classe de la fenêtre que vous souhaitez, vous pouvez les taper dans la **légende** et **classe** zones de texte, puis désactivez la **gérer** zone de texte.  
  
4.  Choisissez **des** ou **vers le bas** pour la direction initiale de la recherche.  
  
5.  Cliquez sur **OK**.  
  
     Si une fenêtre correspondante est trouvée, il est mis en surbrillance dans le [affichage Windows](../debugger/windows-view.md) fenêtre.