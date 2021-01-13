---
title: Rechercher un message dans la vue messages | Microsoft Docs
description: Recherchez un message spécifique dans la vue des messages de l’outil Spy + + en utilisant son handle, son type ou son ID de message en tant que critère de recherche lors du débogage dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c351eacc6fc3793065bcd11eb5456eebdc1864f3
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148583"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Comment : rechercher un message dans la vue Messages
Vous pouvez rechercher un message spécifique dans la vue messages en utilisant son handle, son type ou son ID de message en tant que critère de recherche. L’une d’entre elles (ou une combinaison) sera un critère de recherche valide. La direction initiale de la recherche peut également être spécifiée. Les champs de la boîte de dialogue sont préchargés avec les attributs du message actuellement sélectionné.

### <a name="to-search-for-a-message-in-messages-view"></a>Pour rechercher un message dans la vue messages

1. Réorganisez vos fenêtres afin que Spy + + et une fenêtre d' [affichage des messages](../debugger/messages-view.md) actifs soient visibles.

2. Dans le menu **Rechercher** , choisissez **Rechercher un message**.

    La [boîte de dialogue recherche de message](../debugger/message-search-dialog-box.md) s’ouvre.

3. Faites glisser l' **outil Finder** sur la fenêtre de votre choix. Lorsque vous faites glisser l’outil, la boîte de dialogue **recherche de message** affiche des détails sur la fenêtre sélectionnée.

   - ou -

     Si vous avez le descripteur de la fenêtre dont vous souhaitez examiner les messages, tapez-le dans la zone de texte **handle** .

   - ou -

     Si vous connaissez le type de message et/ou l’ID de message souhaités, sélectionnez-les dans les menus déroulants **type** et **message** , puis désactivez la zone de texte **handle** .

4. Effacez tous les champs pour lesquels vous ne souhaitez pas spécifier de valeurs.

   > [!TIP]
   > Pour réduire l’encombrement de l’écran, sélectionnez l’option **Masquer Spy** . Cette option dissimule la fenêtre principale Spy + +, laissant uniquement la boîte de dialogue **Rechercher une fenêtre** visible en plus de vos autres applications. La fenêtre principale Spy + + est restaurée lorsque vous cliquez sur **OK** ou sur **Annuler**, ou lorsque vous désactivez l’option **Masquer Spy + +** .

5. Choisissez **haut** ou **bas** pour la direction initiale de la recherche.

6. Cliquez sur **OK**.

   Si un message correspondant est trouvé, il est mis en surbrillance dans la fenêtre vue messages. Consultez [affichage des messages](../debugger/messages-view.md).