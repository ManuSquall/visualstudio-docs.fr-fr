---
title: Affichage des messages | Microsoft Docs
description: Chaque fenêtre, thread et processus est associé à un flux de message qui peut être affiché dans une fenêtre d’affichage des messages. Découvrez comment ouvrir et contrôler une vue messages.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 692902b2d2b612c71c2d1dc0f936c7550f430847
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903401"
---
# <a name="messages-view"></a>Affichage Messages
Chaque fenêtre est associée à un flux de message. Une fenêtre d’affichage des messages affiche ce flux de message. Le handle de fenêtre, le code du message et le message sont affichés. Vous pouvez également créer une vue messages pour un thread ou un processus. Cela vous permet d’afficher les messages envoyés à toutes les fenêtres détenues par un processus ou un thread spécifique, ce qui est particulièrement utile pour la capture des messages d’initialisation de fenêtre.

 Une fenêtre d’affichage des messages standard apparaît ci-dessous. Notez que la première colonne contient le handle de fenêtre et que la deuxième colonne contient un code de message (expliqué dans [codes de message](../debugger/message-codes.md)). Les paramètres de message et les valeurs de retour décodés se trouvent à droite.

 ![Affichage des messages de&#43;&#43; Spy](../debugger/media/spy--_messagesview.png "_MessagesView Spy + +") Affichage des messages Spy + +

## <a name="procedures"></a>Procédures

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Pour ouvrir une vue messages pour une fenêtre, un processus ou un thread

1. Déplacer le focus vers une fenêtre vue [fenêtres](../debugger/windows-view.md), [processus](../debugger/processes-view.md)ou [Threads](../debugger/threads-view.md) .

2. Recherchez le nœud de l’élément dont vous souhaitez examiner les messages, puis sélectionnez-le.

3. Dans le menu **Espion** , choisissez **journaux des messages**.

     La [boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md) s’ouvre.

4. Sélectionnez les options du message que vous souhaitez afficher.

5. Appuyez sur **OK** pour commencer l’enregistrement des messages.

     Une fenêtre d’affichage des messages s’ouvre et un menu **messages** est ajouté à la barre d’outils Spy + +. En fonction des options sélectionnées, les messages commencent à diffuser en continu dans la fenêtre Affichage des messages actifs.

6. Lorsque vous avez suffisamment de messages, choisissez **arrêter la journalisation** dans le menu **messages** .

## <a name="in-this-section"></a>Dans cette section
 [Contrôle de la vue messages](../debugger/how-to-control-messages-view.md) Explique comment gérer la vue messages.

 [Ouverture de la vue messages à partir de la fenêtre Rechercher](../debugger/how-to-open-messages-view-from-find-window.md) Explique comment ouvrir la vue messages à partir de la boîte de dialogue Rechercher une fenêtre.

 [Recherche d’un message dans la vue messages](../debugger/how-to-search-for-a-message-in-messages-view.md) Explique comment rechercher un message spécifique dans la vue messages.

 [Démarrage et arrêt de l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md) Explique comment démarrer et arrêter l’enregistrement des messages.

 [Codes des messages](../debugger/message-codes.md) Définit les codes des messages listés dans la vue messages.

 [Affichage des propriétés](../debugger/how-to-display-message-properties.md) d’un message Comment afficher plus d’informations sur un message.

## <a name="related-sections"></a>Sections connexes
 [Vues Spy + +](../debugger/spy-increment-views.md) Explique les vues de l’arborescence Spy + + des fenêtres, des messages, des processus et des threads.

 [Utilisation de Spy + +](../debugger/using-spy-increment.md) Présente l’outil Spy + + et explique comment l’utiliser.

 [Boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md) Permet de sélectionner les messages qui sont répertoriés dans la vue messages actifs.

 [Boîte de dialogue recherche](../debugger/message-search-dialog-box.md) d’un message Utilisé pour rechercher le nœud pour un message spécifique dans la vue messages.

 [Boîte de dialogue Propriétés du message](../debugger/message-properties-dialog-box.md) Permet d’afficher les propriétés d’un message sélectionné dans la vue message.

 [Référence Spy + +](../debugger/spy-increment-reference.md) Comprend des sections décrivant chaque menu et boîte de dialogue Spy + +.