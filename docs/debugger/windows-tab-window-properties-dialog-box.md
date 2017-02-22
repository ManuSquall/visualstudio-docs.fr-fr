---
title: "Onglet Fen&#234;tres de la bo&#238;te de dialogue Propri&#233;t&#233;s de la fen&#234;tre | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Propriétés de la fenêtre (boîte de dialogue), onglet Fenêtres"
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Onglet Fen&#234;tres de la bo&#238;te de dialogue Propri&#233;t&#233;s de la fen&#234;tre
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez l'onglet **Fenêtres** pour afficher les informations relatives aux fenêtres connexes à la fenêtre sélectionnée.  Pour afficher la [boîte de dialogue Propriétés de la fenêtre](../debugger/window-properties-dialog-box.md), déplacez le focus sur la fenêtre [Vue Fenêtres](../debugger/windows-view.md).  Sélectionnez n'importe quel nœud de fenêtre dans l'arborescence, puis sélectionnez **Propriétés** dans le menu **Affichage**.  
  
 Les paramètres suivants sont disponibles sous l'onglet **Fenêtres** :  
  
|Entry|Description|  
|-----------|-----------------|  
|**Fenêtre suivante**|Handle de la fenêtre sœur suivante dans la même séquence \(ordre de plan\) visible dans l'arborescence des fenêtres \("aucun", s'il n'y a pas de fenêtre suivante\).  Choisissez cette entrée pour afficher les propriétés de la fenêtre suivante.|  
|**Fenêtre précédente**|Handle de la fenêtre sœur précédente dans la même séquence \(ordre de plan\) visible dans l'arborescence des fenêtres \("aucun", s'il n'y a pas de fenêtre précédente\).  Choisissez cette entrée pour afficher les propriétés de la fenêtre précédente.|  
|**Fenêtre parente**|Handle de la fenêtre parente de cette fenêtre \("aucun", s'il n'y a aucun parent\).  Choisissez cette entrée pour afficher les propriétés de la fenêtre parente.|  
|**Première fenêtre enfant**|Handle de la première fenêtre enfant de cette fenêtre dans la séquence \(ordre de plan\) visible dans l'arborescence des fenêtres \("aucun", s'il n'y a pas de fenêtres enfants\).  Choisissez cette valeur pour afficher les propriétés de la première fenêtre enfant.|  
|**Fenêtre propriétaire**|Handle de la fenêtre propriétaire de cette fenêtre.  Par exemple, la fenêtre principale d'une application possède généralement des fenêtres de boîtes de dialogue modales système \("aucun", s'il n'y a aucun propriétaire\).  Choisissez cette entrée pour afficher les propriétés de la fenêtre propriétaire.|