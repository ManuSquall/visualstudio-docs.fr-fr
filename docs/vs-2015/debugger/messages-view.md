---
title: Affichage des messages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3765b9804224549c98b57cd1b0a44f0330d278b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157490"
---
# <a name="messages-view"></a>Affichage Messages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chaque fenêtre est associée à un flux de message. Une fenêtre d’affichage des messages affiche ce flux de message. Le handle de fenêtre, le code du message et le message sont affichés. Vous pouvez également créer une vue messages pour un thread ou un processus. Cela vous permet d’afficher les messages envoyés à toutes les fenêtres détenues par un processus ou un thread spécifique, ce qui est particulièrement utile pour la capture des messages d’initialisation de fenêtre.  
  
 Une fenêtre d’affichage des messages standard apparaît ci-dessous. Notez que la première colonne contient le handle de fenêtre et que la deuxième colonne contient un code de message (expliqué dans [codes de message](../debugger/message-codes.md)). Les paramètres de message et les valeurs de retour décodés se trouvent à droite.  
  
 ![Affichage des messages de&#43;&#43; Spy](../debugger/media/spy-messagesview.png "_MessagesView Spy + +")  
Vue Messages Spy++  
  
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
 [Contrôle de la vue messages](../debugger/how-to-control-messages-view.md)  
 Explique comment gérer la vue messages.  
  
 [Recherche d’un message dans la vue messages](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Explique comment rechercher un message spécifique dans la vue messages.  
  
 [Démarrage et arrêt de l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Explique comment démarrer et arrêter l’enregistrement des messages.  
  
 [Codes des messages](../debugger/message-codes.md)  
 Définit les codes des messages listés dans la vue messages.  
  
 [Affichage des propriétés d’un message](../debugger/how-to-display-message-properties.md)  
 Comment afficher plus d’informations sur un message.  
  
## <a name="related-sections"></a>Sections connexes  
 [Vues Spy++](../debugger/spy-increment-views.md)  
 Explique les vues de l’arborescence Spy + + des fenêtres, des messages, des processus et des threads.  
  
 [Utiliser Spy++](../debugger/using-spy-increment.md)  
 Présente l’outil Spy + + et explique comment l’utiliser.  
  
 [Options des messages, boîte de dialogue](../debugger/message-options-dialog-box.md)  
 Permet de sélectionner les messages qui sont répertoriés dans la vue messages actifs.  
  
 [Boîte de dialogue Recherche d'un message](../debugger/message-search-dialog-box.md)  
 Utilisé pour rechercher le nœud pour un message spécifique dans la vue messages.  
  
 [Boîte de dialogue Propriétés du message](../debugger/message-properties-dialog-box.md)  
 Permet d’afficher les propriétés d’un message sélectionné dans la vue message.  
  
 [Référence Spy++](../debugger/spy-increment-reference.md)  
 Comprend des sections décrivant chaque menu et boîte de dialogue Spy + +.
