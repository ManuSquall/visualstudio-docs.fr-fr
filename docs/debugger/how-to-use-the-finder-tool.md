---
title: 'Comment : utiliser l’outil recherche | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f358adbd8721a55d278c392018463d49e5a8a60e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-use-the-finder-tool"></a>Comment : utiliser l'outil Recherche
Vous pouvez utiliser l’outil de recherche dans les **rechercher une fenêtre** boîte de dialogue pour afficher la fenêtre Propriétés ou messages. L’outil recherche peut également localiser les fenêtres enfants désactivées et déterminer la fenêtre à mettre en surbrillance si désactivé enfant windows chevauchement.  
  
 ![Spy&#43; &#43; boîte de dialogue de fenêtre Rechercher](../debugger/media/icon_spy--_find.png "Icon_Spy ++ _Find")  
Outil de recherche dans la boîte de dialogue Rechercher une fenêtre  
  
 La figure ci-dessus illustre la boîte de dialogue Rechercher une fenêtre après l’étape 3 ci-dessous.  
  
### <a name="to-display-window-properties-or-messages"></a>Pour afficher la fenêtre Propriétés ou messages  
  
1.  Réorganisez vos fenêtres afin que Spy ++ et la fenêtre cible sont visibles.  
  
2.  À partir de la **Spy** menu, choisissez **rechercher une fenêtre**.  
  
     Le [boîte de dialogue Rechercher une fenêtre](../debugger/find-window-dialog-box.md) s’ouvre.  
  
3.  Faites glisser le **outil recherche** sur la fenêtre cible.  
  
     Lorsque vous faites glisser l’outil, le **rechercher une fenêtre** boîte de dialogue affiche des informations sur la fenêtre sélectionnée.  
  
     - ou  
  
     Si vous avez le handle de la fenêtre que vous souhaitez examiner (par exemple, copié à partir du débogueur), tapez-le dans la **gérer** zone de texte.  
  
    > [!TIP]
    >  Pour réduire l’encombrement de l’écran, sélectionnez le **Masquer Spy ++** option. Cette option masque la fenêtre Spy ++ principale, en laissant uniquement le **rechercher une fenêtre** boîte de dialogue visible au-dessus de vos autres applications. La fenêtre principale Spy ++ est restaurée lorsque vous cliquez sur **OK** ou **Annuler**, ou lorsque vous désactivez le **Masquer Spy ++** option.  
  
4.  Sous **afficher**, sélectionnez **propriétés** ou **Messages**.  
  
5.  Press **OK**.  
  
     Si vous avez sélectionné **propriétés**, le [boîte de dialogue Propriétés de fenêtre](../debugger/window-properties-dialog-box.md) s’ouvre. Si vous avez sélectionné **Messages**, un [vue Messages](../debugger/messages-view.md) fenêtre s’ouvre.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues Spy ++](../debugger/spy-increment-views.md)   
 [À l’aide de Spy ++](../debugger/using-spy-increment.md)   
 [Informations de référence sur Spy++](../debugger/spy-increment-reference.md)