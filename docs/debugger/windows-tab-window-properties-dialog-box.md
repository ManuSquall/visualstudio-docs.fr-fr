---
title: Onglet de Windows, la boîte de dialogue Propriétés de fenêtre | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce1015741b2a1e7ba1608eea7f198b726e808f7f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900781"
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
