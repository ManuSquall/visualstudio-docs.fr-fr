---
title: La vue messages | Microsoft Docs
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
ms.openlocfilehash: db9d64119a94e2358a6f52e6e1269fca8d726cbb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694398"
---
# <a name="messages-view"></a>Affichage Messages
Chaque fenêtre a un flux de message associé. Une fenêtre d’affichage de Messages affiche ce flux de message. Le handle de fenêtre, le code de message et le message sont affichés. Vous pouvez créer un affichage de Messages pour un thread ou un processus. Cela vous permet de vous permet d’afficher les messages envoyés à toutes les fenêtres appartenant à un processus spécifique ou un thread, qui est particulièrement utile pour capturer les messages de l’initialisation de fenêtre.

 Une fenêtre d’affichage de Messages standard s’affiche ci-dessous. Notez que la première colonne contient le handle de fenêtre et la deuxième colonne contient un code de message (expliqué dans [Codes des messages](../debugger/message-codes.md)). Paramètres de message décodés et les valeurs de retour sont sur la droite.

 ![Spy&#43; &#43; la vue Messages](../debugger/media/spy--_messagesview.png "Spy ++ _MessagesView") Spy ++ la vue Messages

## <a name="procedures"></a>Procédures

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Pour ouvrir un affichage de Messages pour une fenêtre, un processus ou un thread

1.  Déplacer le focus à un [Windows vue](../debugger/windows-view.md), [vue processus](../debugger/processes-view.md), ou [vue Threads](../debugger/threads-view.md) fenêtre.

2.  Recherchez le nœud de l’élément dont vous souhaitez examiner les messages, puis sélectionnez-le.

3.  À partir de la **Spy** menu, choisissez **Messages du journal**.

     Le [la boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md) s’ouvre.

4.  Sélectionnez les options pour le message que vous souhaitez afficher.

5.  Appuyez sur **OK** pour commencer la journalisation des messages.

     Ouvre la fenêtre d’affichage des Messages, ainsi qu’un **Messages** menu est ajouté à la barre d’outils Spy ++. Selon les options sélectionnées, messages commencent le streaming dans la fenêtre d’affichage de Messages active.

6.  Lorsque vous avez suffisamment de messages, choisissez **Stop Logging** à partir de la **Messages** menu.

## <a name="in-this-section"></a>Dans cette section
 [Contrôler la vue Messages](../debugger/how-to-control-messages-view.md) explique comment gérer la vue Messages.

 [Ouvrir la vue Messages à partir de la fenêtre Rechercher](../debugger/how-to-open-messages-view-from-find-window.md) explique comment ouvrir la vue Messages à partir de la boîte de dialogue Rechercher une fenêtre.

 [Recherche d’un Message dans la vue Messages](../debugger/how-to-search-for-a-message-in-messages-view.md) explique comment rechercher un message spécifique dans la vue Messages.

 [Démarrage et arrêt de l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md) explique comment démarrer et arrêter la journalisation des messages.

 [Codes de message](../debugger/message-codes.md) définit les codes pour les messages répertoriés dans la vue Messages.

 [Affichage des propriétés de Message](../debugger/how-to-display-message-properties.md) comment afficher plus d’informations sur un message.

## <a name="related-sections"></a>Rubriques connexes
 [Vues Spy ++](../debugger/spy-increment-views.md) explique les arborescences Spy ++ de windows, les messages, les processus et les threads.

 [À l’aide de Spy ++](../debugger/using-spy-increment.md) présente l’outil Spy ++ et explique comment il peut être utilisé.

 [Boîte de dialogue Options du message](../debugger/message-options-dialog-box.md) permet de sélectionner les messages sont répertoriés dans la vue Messages active.

 [Boîte de dialogue de recherche du message](../debugger/message-search-dialog-box.md) utilisé pour rechercher le nœud pour un message spécifique dans la vue Messages.

 [Boîte de dialogue Propriétés du message](../debugger/message-properties-dialog-box.md) utilisé pour afficher les propriétés d’un message sélectionné dans la vue de Message.

 [Référence Spy ++](../debugger/spy-increment-reference.md) comprend les sections décrivant chaque Spy ++ menu et boîte de dialogue.