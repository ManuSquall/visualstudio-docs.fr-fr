---
title: Ouvrir la vue messages à partir de la fenêtre Rechercher | Microsoft Docs
description: Utilisez la boîte de dialogue Rechercher une fenêtre dans Spy + + pour sélectionner une fenêtre cible, puis ouvrez une vue messages pour cette fenêtre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e66e3e1200e1e08776853f2ac8308537e4b4a17
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148908"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Comment : ouvrir la vue Messages à partir de Rechercher une fenêtre
Il peut s’avérer pratique d’utiliser la boîte de dialogue **Rechercher** une fenêtre pour sélectionner une fenêtre cible, puis d’ouvrir une vue messages de cette fenêtre.

### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Pour ouvrir une fenêtre d’affichage des messages à l’aide de la boîte de dialogue Rechercher une fenêtre

1. Réorganisez vos fenêtres de manière à ce que Spy + + et la fenêtre cible soient visibles.

2. Dans le menu **Espion** , choisissez **Rechercher une fenêtre**.

    La [boîte de dialogue Rechercher une fenêtre](../debugger/find-window-dialog-box.md) s’ouvre.

3. À partir de l’onglet **Windows** , faites glisser l' **outil recherche** sur la fenêtre cible. Lorsque vous faites glisser l’outil, la boîte de dialogue **Rechercher une fenêtre** affiche des détails sur la fenêtre sélectionnée.

   - ou -

     Si vous avez le handle de la fenêtre que vous souhaitez examiner (par exemple, copié à partir du débogueur), vous pouvez le taper dans la zone de texte **handle** .

4. Sous **Afficher**, sélectionnez **messages**.

5. Appuyez sur **OK**.

    Une fenêtre d' [affichage des messages](../debugger/messages-view.md) vide s’ouvre et un menu **messages** est ajouté à la barre d’outils Spy + +.

6. Dans le menu **messages** , choisissez **options de journalisation**.

    La [boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md) s’ouvre.

7. Sélectionnez les options pour les messages que vous souhaitez afficher.

8. Appuyez sur **OK** pour commencer l’enregistrement des messages.

    En fonction des options sélectionnées, les messages commencent à diffuser en continu dans la fenêtre Affichage des messages actifs.

9. Lorsque vous avez suffisamment de messages, choisissez **arrêter la journalisation** dans le menu **messages** .
