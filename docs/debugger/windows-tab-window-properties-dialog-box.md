---
title: "Onglet Windows, la boîte de dialogue Propriétés de fenêtre | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a49ec9b52d2eaf6dc336ed28d5b4e531bb3b25cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="windows-tab-window-properties-dialog-box"></a>Onglet Fenêtres de la boîte de dialogue Propriétés de la fenêtre
Utilisez le **Windows** onglet pour afficher des informations sur windows liées à la fenêtre sélectionnée. Pour afficher le [boîte de dialogue Propriétés de fenêtre](../debugger/window-properties-dialog-box.md), déplacer le focus vers le [affichage Windows](../debugger/windows-view.md) fenêtre. Sélectionnez n’importe quel nœud de fenêtre dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **Windows** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Fenêtre suivante**|Le handle de la fenêtre de frère suivant dans la même séquence (ordre de plan) indiquée dans l’arborescence des fenêtres (« aucun », s’il n’existe pas de fenêtre suivante). Choisissez cette entrée pour afficher les propriétés de la fenêtre suivante.|  
|**Fenêtre précédente**|Le handle de la fenêtre de frère précédent dans la même séquence (ordre de plan) indiquée dans l’arborescence des fenêtres (« aucun », s’il n’existe pas de fenêtre précédente). Choisissez cette entrée pour afficher les propriétés de la fenêtre précédente.|  
|**Fenêtre parente**|Handle de cette fenêtre parente (« aucun », s’il n’existe aucun parent). Choisissez cette entrée pour afficher les propriétés de la fenêtre parente.|  
|**Premier enfant**|Le handle de première fenêtre enfant cette fenêtre, dans la séquence (ordre de plan) indiqué dans l’arborescence des fenêtres (« aucun », si aucune fenêtre enfant). Choisissez cette valeur pour afficher les propriétés de la première fenêtre enfant.|  
|**Fenêtre propriétaire**|Le handle de fenêtre propriétaire de cette fenêtre. Fenêtre principale d’une application possède généralement des fenêtres de boîtes de dialogue modales du système, par exemple (« aucun », s’il n’existe aucun propriétaire). Choisissez cette entrée pour afficher les propriétés de la fenêtre propriétaire.|