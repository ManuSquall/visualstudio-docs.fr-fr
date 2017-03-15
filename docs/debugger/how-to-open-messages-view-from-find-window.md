---
title: "Comment&#160;: ouvrir la vue Messages &#224; partir de Rechercher une fen&#234;tre | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vue Messages dans Spy++, ouverture"
  - "ouvrir la vue Messages dans Spy++"
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Comment&#160;: ouvrir la vue Messages &#224; partir de Rechercher une fen&#234;tre
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous avez la possibilité d'utiliser la boîte de dialogue **Rechercher une fenêtre** pour sélectionner une fenêtre cible et ouvrir une vue Messages de cette fenêtre.  
  
### Pour ouvrir une fenêtre Vue Messages à l'aide de la boîte de dialogue Rechercher une fenêtre  
  
1.  Réorganisez vos fenêtres afin que Spy\+\+ et la fenêtre cible soient visibles.  
  
2.  Dans le menu **Espionner**, choisissez **Rechercher une fenêtre**.  
  
     La [boîte de dialogue Rechercher une fenêtre](../debugger/find-window-dialog-box.md) s'ouvre.  
  
3.  À partir de l'onglet **Fenêtres**, faites glisser l'**outil Recherche** sur la fenêtre cible.  Lorsque vous faites glisser l'outil, la boîte de dialogue **Rechercher une fenêtre** affiche des informations sur la fenêtre sélectionnée.  
  
     \- ou \-  
  
     Si vous disposez du handle de la fenêtre à examiner \(copié à partir du débogueur, par exemple\), tapez\-le dans la zone de texte **Handle**.  
  
4.  Sous **Afficher**, sélectionnez **Messages**.  
  
5.  Cliquez sur **OK**.  
  
     Une fenêtre [Vue Messages](../debugger/messages-view.md) vide s'ouvre, et un menu **Messages** est ajouté à la barre d'outils Spy\+\+.  
  
6.  Dans le menu **Messages**, choisissez **Options du journal**.  
  
     La [boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md) s'ouvre.  
  
7.  Sélectionnez les options des messages à afficher.  
  
8.  Appuyez sur **OK** pour commencer l'enregistrement des messages.  
  
     En fonction des options sélectionnées, les messages commencent à être diffusés en continu dans la fenêtre Vue Messages active.  
  
9. Lorsque vous avez suffisamment de messages, sélectionnez **Arrêter l'enregistrement** dans le menu **Messages**.