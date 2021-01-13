---
title: Utiliser l’outil Finder | Microsoft Docs
description: Utilisez l’outil recherche de la boîte de dialogue Rechercher une fenêtre de l’outil Spy + + pour afficher les propriétés ou les messages de la fenêtre pendant une session de débogage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41ca277962f81b3cd1c35ebcf8a940e8168a6803
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150598"
---
# <a name="how-to-use-the-finder-tool"></a>Comment : utiliser l'outil Recherche
Vous pouvez utiliser l’outil recherche de la boîte de dialogue **Rechercher une fenêtre** pour afficher des propriétés ou des messages de la fenêtre. L’outil Finder peut également localiser les fenêtres enfants désactivées et déterminer la fenêtre à mettre en évidence si les fenêtres enfants désactivées se chevauchent.

 ![Boîte de dialogue Rechercher une fenêtre de&#43;&#43; Spy](../debugger/media/icon_spy--_find.png "_Find Icon_Spy + +") Outil Finder dans la boîte de dialogue Rechercher une fenêtre

 La figure ci-dessus illustre la boîte de dialogue Rechercher une fenêtre après l’étape 3 ci-dessous.

### <a name="to-display-window-properties-or-messages"></a>Pour afficher les propriétés ou les messages d’une fenêtre

1. Réorganisez vos fenêtres de manière à ce que Spy + + et la fenêtre cible soient visibles.

2. Dans le menu **Espion** , choisissez **Rechercher une fenêtre**.

    La [boîte de dialogue Rechercher une fenêtre](../debugger/find-window-dialog-box.md) s’ouvre.

3. Faites glisser l' **outil recherche** sur la fenêtre cible.

    Lorsque vous faites glisser l’outil, la boîte de dialogue **Rechercher une fenêtre** affiche des détails sur la fenêtre sélectionnée.

   - ou -

     Si vous avez le handle de la fenêtre que vous souhaitez examiner (par exemple, copié à partir du débogueur), tapez-le dans la zone de texte **handle** .

   > [!TIP]
   > Pour réduire l’encombrement de l’écran, sélectionnez l’option **Masquer Spy** . Cette option dissimule la fenêtre principale Spy + +, laissant uniquement la boîte de dialogue **Rechercher une fenêtre** visible en plus de vos autres applications. La fenêtre principale Spy + + est restaurée lorsque vous cliquez sur **OK** ou sur **Annuler**, ou lorsque vous désactivez l’option **Masquer Spy + +** .

4. Sous **Afficher**, sélectionnez **Propriétés** ou **messages**.

5. Appuyez sur **OK**.

    Si vous avez sélectionné **Propriétés**, la [boîte de dialogue Propriétés](../debugger/window-properties-dialog-box.md) de la fenêtre s’ouvre. Si vous avez sélectionné **messages**, une fenêtre d' [affichage des messages](../debugger/messages-view.md) s’ouvre.

## <a name="see-also"></a>Voir aussi
- [Vues Spy++](../debugger/spy-increment-views.md)
- [Utiliser Spy++](../debugger/using-spy-increment.md)
- [Référence Spy++](../debugger/spy-increment-reference.md)