---
title: Rechercher une fenêtre dans la vue fenêtres | Microsoft Docs
description: Recherchez une fenêtre spécifique dans la vue Windows de l’outil Spy + + à l’aide de son handle, d’une légende, d’une classe ou d’une combinaison de sa légende et de sa classe dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0051a17d3a2360776f48cee2bd7f1d2f11a2492
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920097"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Comment : rechercher une fenêtre dans la vue Fenêtres
Vous pouvez rechercher une fenêtre spécifique dans la vue Windows en utilisant son handle, sa légende, sa classe ou une combinaison de sa légende et de sa classe en tant que critère de recherche. Vous pouvez également spécifier le sens initial de la recherche. Les champs de la boîte de dialogue affichent les attributs de la fenêtre sélectionnée dans l’arborescence de la fenêtre.

 Commencez par l’arborescence développée jusqu’au deuxième niveau (toutes les fenêtres qui sont des enfants du bureau), afin de pouvoir identifier les fenêtres au niveau du Bureau en fonction de leur nom de classe et de leur titre. Une fois que vous avez choisi une fenêtre au niveau du bureau, vous pouvez développer ce niveau pour rechercher une fenêtre enfant spécifique.

### <a name="to-search-for-a-window-in-windows-view"></a>Pour rechercher une fenêtre dans la vue fenêtres

1. Réorganisez vos fenêtres de manière à ce que Spy + +, la fenêtre [vue Windows](../debugger/windows-view.md) et la fenêtre cible soient visibles.

2. Dans le menu **Rechercher** , choisissez **Rechercher une fenêtre**.

    La [boîte de dialogue recherche de fenêtre](../debugger/window-search-dialog-box.md) s’ouvre.

   > [!TIP]
   > Pour réduire l’encombrement de l’écran, sélectionnez l’option **Masquer Spy** . Cette option permet de masquer la fenêtre principale de Spy + + et laisse uniquement la boîte de dialogue **recherche de fenêtre** visible en plus de vos autres applications. La fenêtre principale Spy + + est restaurée lorsque vous cliquez sur **OK** ou sur **Annuler**, ou lorsque vous désactivez l’option **Masquer Spy + +** .

3. Faites glisser l' **outil recherche** sur la fenêtre cible. Lorsque vous faites glisser l’outil, la boîte de dialogue **recherche de fenêtre** affiche des détails sur la fenêtre sélectionnée.

   - ou -

     Si vous connaissez le descripteur de la fenêtre de votre choix (par exemple, à partir du débogueur), vous pouvez le taper dans la zone **handle** .

   - ou -

     Si vous connaissez la légende et/ou la classe de la fenêtre souhaitée, vous pouvez les taper dans les zones de texte **légende** et **classe** et effacer la zone de texte **handle** .

4. Choisissez **haut** ou **bas** pour la direction initiale de la recherche.

5. Cliquez sur **OK**.

    Si une fenêtre correspondante est trouvée, elle est mise en surbrillance dans la fenêtre [vue Windows](../debugger/windows-view.md) .