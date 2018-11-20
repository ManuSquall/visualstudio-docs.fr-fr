---
title: La vue messages | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f896650d7979365346d493c5aac06340007cbb7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784375"
---
# <a name="messages-view"></a>Affichage Messages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chaque fenêtre a un flux de message associé. Une fenêtre d’affichage de Messages affiche ce flux de message. Le handle de fenêtre, le code de message et le message sont affichés. Vous pouvez créer un affichage de Messages pour un thread ou un processus. Cela vous permet de vous permet d’afficher les messages envoyés à toutes les fenêtres appartenant à un processus spécifique ou un thread, qui est particulièrement utile pour capturer les messages de l’initialisation de fenêtre.  
  
 Une fenêtre d’affichage de Messages standard s’affiche ci-dessous. Notez que la première colonne contient le handle de fenêtre et la deuxième colonne contient un code de message (expliqué dans [Codes des messages](../debugger/message-codes.md)). Paramètres de message décodés et les valeurs de retour sont sur la droite.  
  
 ![Spy&#43; &#43; la vue Messages](../debugger/media/spy-messagesview.png "Spy ++ _MessagesView")  
Messages Spy++, vue  
  
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
 [Contrôler la vue Messages](../debugger/how-to-control-messages-view.md)  
 Explique comment gérer la vue Messages.  
  
 [Recherche d’un Message dans la vue Messages](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Explique comment rechercher un message spécifique dans la vue Messages.  
  
 [Démarrage et arrêt de l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Explique comment démarrer et arrêter la journalisation des messages.  
  
 [Codes des messages](../debugger/message-codes.md)  
 Définit les codes des messages répertoriés dans la vue Messages.  
  
 [Affichage des propriétés de Message](../debugger/how-to-display-message-properties.md)  
 Guide pratique pour afficher plus d’informations sur un message.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Vues Spy++](../debugger/spy-increment-views.md)  
 Explique les arborescences Spy ++ de windows, les messages, les processus et les threads.  
  
 [Utilisation de Spy++](../debugger/using-spy-increment.md)  
 Présente l’outil Spy ++ et explique comment il peut être utilisé.  
  
 [Options des messages, boîte de dialogue](../debugger/message-options-dialog-box.md)  
 Permet de sélectionner les messages sont répertoriés dans la vue Messages active.  
  
 [Recherche d’un message, boîte de dialogue](../debugger/message-search-dialog-box.md)  
 Utilisé pour rechercher le nœud pour un message spécifique dans la vue Messages.  
  
 [Propriétés du message, boîte de dialogue](../debugger/message-properties-dialog-box.md)  
 Permet d’afficher les propriétés d’un message sélectionné dans la vue de Message.  
  
 [Informations de référence sur Spy++](../debugger/spy-increment-reference.md)  
 Inclut des sections décrivant chaque Spy ++ menu et boîte de dialogue.



