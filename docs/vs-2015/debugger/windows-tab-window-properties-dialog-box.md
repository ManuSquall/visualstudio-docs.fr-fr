---
title: Onglet de Windows, la boîte de dialogue Propriétés de fenêtre | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9546be8fd50daea8369b00ae9bbc1eab2427c9c9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297217"
---
# <a name="windows-tab-window-properties-dialog-box"></a>Onglet Fenêtres de la boîte de dialogue Propriétés de la fenêtre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilisez le **Windows** onglet pour afficher des informations sur windows liés à la fenêtre sélectionnée. Pour afficher le [boîte de dialogue Propriétés de fenêtre](../debugger/window-properties-dialog-box.md), déplacer le focus vers le [Windows vue](../debugger/windows-view.md) fenêtre. Sélectionnez n’importe quel nœud de fenêtre dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **Windows** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Fenêtre suivante**|Le handle de la fenêtre de frère suivant dans la même séquence (ordre de plan) indiquée dans l’arborescence de fenêtre (« none », s’il n’existe aucune fenêtre suivante). Choisissez cette entrée pour afficher les propriétés de la fenêtre suivante.|  
|**Fenêtre précédente**|Le handle de la fenêtre de frère précédent dans le même ordre (Z-order) indiqué dans l’arborescence de fenêtre (« none », s’il n’existe aucune fenêtre précédente). Choisissez cette entrée pour afficher les propriétés de la fenêtre précédente.|  
|**Fenêtre parente**|Handle de cette fenêtre parente (« none », s’il n’existe aucun parent). Choisissez cette entrée pour afficher les propriétés de la fenêtre parente.|  
|**Premier enfant**|Handle de première fenêtre enfant cette fenêtre, dans la séquence (Z-order) indiqué dans l’arborescence de fenêtre (« none », si aucune fenêtre enfant). Choisissez cette valeur pour afficher les propriétés de la première fenêtre enfant.|  
|**Fenêtre propriétaire**|Le handle de fenêtre de propriétaire de cette fenêtre. Fenêtre principale d’une application possède généralement des fenêtres de boîte de dialogue modale du système, par exemple (« none », s’il n’existe aucun propriétaire). Choisissez cette entrée pour afficher les propriétés de la fenêtre propriétaire.|



