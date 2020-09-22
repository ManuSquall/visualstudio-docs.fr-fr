---
title: Ouvrir la vue messages à partir de la fenêtre Rechercher | Microsoft Docs
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
ms.openlocfilehash: 9b6240807eb82313182278251b353894545b957d
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852268"
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
