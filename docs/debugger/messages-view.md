---
title: "Messages View | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.externaltools.spyplus.messagesview"
helpviewer_keywords: 
  - "Messages view"
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Messages View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Chaque fenêtre a un flux de messages associé.  Une fenêtre Vue Messages affiche ce flux de messages.  Le handle de fenêtre, le code du message et le message sont affichés.  Vous pouvez également créer une vue Messages pour un thread ou un processus.  Cela vous permet d'afficher les messages envoyés à toutes les fenêtres détenues par un processus ou un thread spécifique, ce qui est particulièrement utile pour la capture de messages d'initialisation de fenêtres.  
  
 Une fenêtre Vue Messages classique est représentée ci\-dessous.  Notez que la première colonne contient le handle de fenêtre et que la deuxième colonne contient un code de message \(expliqué dans [Codes des messages](../debugger/message-codes.md)\).  Les paramètres de message décodés et les valeurs de retour sont à droite.  
  
 ![Messages Spy&#43;&#43;, vue](../debugger/media/spy--_messagesview.png "Spy\+\+\_MessagesView")  
Vue Messages Spy\+\+  
  
## Procédures  
  
#### Pour ouvrir une vue Messages pour une fenêtre, un processus ou un thread  
  
1.  Déplacez le focus vers une fenêtre [Vue Fenêtres](../debugger/windows-view.md), [Vue Processus](../debugger/processes-view.md) ou [Vue Threads](../debugger/threads-view.md).  
  
2.  Recherchez le nœud de l'élément dont vous voulez examiner les messages, puis sélectionnez\-le.  
  
3.  Dans le menu **Espionner**, choisissez **Enregistrer les messages**.  
  
     La [boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md) s'ouvre.  
  
4.  Sélectionnez les options du message à afficher.  
  
5.  Appuyez sur **OK** pour commencer l'enregistrement des messages.  
  
     Une fenêtre Vue Messages s'ouvre, et un menu **Messages** est ajouté à la barre d'outils Spy\+\+.  En fonction des options sélectionnées, les messages commencent à être diffusés en continu dans la fenêtre Vue Messages active.  
  
6.  Lorsque vous avez suffisamment de messages, sélectionnez **Arrêter l'enregistrement** dans le menu **Messages**.  
  
## Dans cette section  
 [Contrôle de la vue Messages](../debugger/how-to-control-messages-view.md)  
 Explique comment gérer la vue Messages.  
  
 [Ouverture de la vue Messages à partir de Rechercher une fenêtre](_asug_choosing_message_options)  
 Explique comment ouvrir la vue Messages à partir de la boîte de dialogue Rechercher une fenêtre.  
  
 [Recherche d'un message dans la vue Messages](../Topic/How%20to:%20Search%20for%20a%20Message%20in%20Messages%20View.md)  
 Explique comment rechercher un message spécifique dans la vue Messages.  
  
 [Démarrage et arrêt de l'affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Explique comment démarrer et arrêter l'enregistrement des messages.  
  
 [Codes des messages](../debugger/message-codes.md)  
 Définit les codes des messages répertoriés dans la vue Messages.  
  
 [Affichage des propriétés d'un message](../debugger/how-to-display-message-properties.md)  
 Explique comment afficher davantage d'informations sur un message.  
  
## Rubriques connexes  
 [Vues Spy\+\+](../debugger/spy-increment-views.md)  
 Explique les arborescences Spy\+\+ des fenêtres, messages, processus et threads.  
  
 [Utilisation de Spy\+\+](../debugger/using-spy-increment.md)  
 Présente l'outil Spy\+\+ et explique comment l'utiliser.  
  
 [Boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md)  
 Permet de sélectionner les messages répertoriés dans la vue Messages active.  
  
 [Boîte de dialogue Recherche d'un message](../debugger/message-search-dialog-box.md)  
 Permet de rechercher le nœud d'un message spécifique dans la vue Messages.  
  
 [Boîte de dialogue Propriétés du message](../debugger/message-properties-dialog-box.md)  
 Permet d'afficher les propriétés d'un message sélectionné dans la vue Messages.  
  
 [Référence de Spy\+\+](../debugger/spy-increment-reference.md)  
 Inclut des sections décrivant les menus et les boîtes de dialogue de Spy\+\+.