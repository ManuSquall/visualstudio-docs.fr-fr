---
title: 'Comment : Rechercher une fenêtre dans la vue fenêtres | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d9d7a64191db82d5fb0b82518d3db1cf1eb1e0ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840253"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Comment : rechercher une fenêtre dans la vue Fenêtres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez rechercher une fenêtre spécifique dans la vue Windows en utilisant son handle, sa légende, sa classe ou une combinaison de sa légende et de sa classe en tant que critère de recherche. Vous pouvez également spécifier le sens initial de la recherche. Les champs de la boîte de dialogue affichent les attributs de la fenêtre sélectionnée dans l’arborescence de la fenêtre.  
  
 Commencez par l’arborescence développée jusqu’au deuxième niveau (toutes les fenêtres qui sont des enfants du bureau), afin de pouvoir identifier les fenêtres au niveau du Bureau en fonction de leur nom de classe et de leur titre. Une fois que vous avez choisi une fenêtre au niveau du bureau, vous pouvez développer ce niveau pour rechercher une fenêtre enfant spécifique.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Pour rechercher une fenêtre dans la vue fenêtres  
  
1. Réorganisez vos fenêtres de manière à ce que Spy + +, la fenêtre [vue Windows](../debugger/windows-view.md) et la fenêtre cible soient visibles.  
  
2. Dans le menu **Rechercher** , choisissez **Rechercher une fenêtre**.  
  
     La [boîte de dialogue recherche de fenêtre](../debugger/window-search-dialog-box.md) s’ouvre.  
  
    > [!TIP]
    > Pour réduire l’encombrement de l’écran, sélectionnez l’option **Masquer Spy** . Cette option permet de masquer la fenêtre principale de Spy + + et laisse uniquement la boîte de dialogue **recherche de fenêtre** visible en plus de vos autres applications. La fenêtre principale Spy + + est restaurée lorsque vous cliquez sur **OK** ou sur **Annuler**, ou lorsque vous désactivez l’option **Masquer Spy + +** .  
  
3. Faites glisser l' **outil recherche** sur la fenêtre cible. Lorsque vous faites glisser l’outil, la boîte de dialogue **recherche de fenêtre** affiche des détails sur la fenêtre sélectionnée.  
  
     – ou –  
  
     Si vous connaissez le descripteur de la fenêtre de votre choix (par exemple, à partir du débogueur), vous pouvez le taper dans la zone **handle** .  
  
     – ou –  
  
     Si vous connaissez la légende et/ou la classe de la fenêtre souhaitée, vous pouvez les taper dans les zones de texte **légende** et **classe** et effacer la zone de texte **handle** .  
  
4. Choisissez **haut** ou **bas** pour la direction initiale de la recherche.  
  
5. Cliquez sur **OK**.  
  
     Si une fenêtre correspondante est trouvée, elle est mise en surbrillance dans la fenêtre [vue Windows](../debugger/windows-view.md) .
