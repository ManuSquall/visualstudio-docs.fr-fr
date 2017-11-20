---
title: "Comment : ouvrir la vue Messages à partir de la fenêtre Rechercher | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f69a79cbc80df206cd1c12abc9a34aa78eeb6194
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-open-messages-view-from-find-window"></a>Comment : ouvrir la vue Messages à partir de Rechercher une fenêtre
Il peut s’avérer pratique d’utiliser le **rechercher une fenêtre** boîte de dialogue pour sélectionner une fenêtre cible, puis ouvrez un affichage de Messages de cette fenêtre.  
  
### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Pour ouvrir une fenêtre d’affichage de Messages à l’aide de la boîte de dialogue Rechercher une fenêtre  
  
1.  Réorganisez vos fenêtres afin que Spy ++ et la fenêtre cible sont visibles.  
  
2.  À partir de la **Spy** menu, choisissez **rechercher une fenêtre**.  
  
     Le [boîte de dialogue Rechercher une fenêtre](../debugger/find-window-dialog-box.md) s’ouvre.  
  
3.  À partir de la **Windows** onglet, faites glisser le **outil recherche** sur la fenêtre cible. Lorsque vous faites glisser l’outil, le **rechercher une fenêtre** boîte de dialogue affiche des informations sur la fenêtre sélectionnée.  
  
     - ou  
  
     Si vous avez le handle de la fenêtre que vous souhaitez examiner (par exemple, copié à partir du débogueur), vous pouvez la taper dans le **gérer** zone de texte.  
  
4.  Sous **afficher**, sélectionnez **Messages**.  
  
5.  Press **OK**.  
  
     Une valeur vide [vue Messages](../debugger/messages-view.md) fenêtre s’ouvre et un **Messages** menu est ajouté à la barre d’outils Spy ++.  
  
6.  À partir de la **Messages** menu, choisissez **des Options de journalisation**.  
  
     Le [la boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md) s’ouvre.  
  
7.  Sélectionnez les options pour les messages que vous souhaitez afficher.  
  
8.  Appuyez sur **OK** pour commencer l’enregistrement des messages.  
  
     Selon les options sélectionnées, les messages commencent de diffusion en continu dans la fenêtre d’affichage de Messages active.  
  
9. Lorsque vous avez suffisamment de messages, sélectionnez **Stop Logging** à partir de la **Messages** menu.