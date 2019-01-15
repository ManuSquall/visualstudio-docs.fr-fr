---
title: Onglet de Windows, la boîte de dialogue Propriétés de fenêtre | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 50b3bb42613fd28741ea6541a13ad08e3d12b97a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949983"
---
# <a name="windows-tab-window-properties-dialog-box"></a>Onglet Fenêtres de la boîte de dialogue Propriétés de la fenêtre
Utilisez le **Windows** onglet pour afficher des informations sur windows liés à la fenêtre sélectionnée. Pour afficher le [boîte de dialogue Propriétés de fenêtre](../debugger/window-properties-dialog-box.md), déplacer le focus vers le [Windows vue](../debugger/windows-view.md) fenêtre. Sélectionnez n’importe quel nœud de fenêtre dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **Windows** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Fenêtre suivante**|Le handle de la fenêtre de frère suivant dans la même séquence (ordre de plan) indiquée dans l’arborescence de fenêtre (« none », s’il n’existe aucune fenêtre suivante). Choisissez cette entrée pour afficher les propriétés de la fenêtre suivante.|  
|**Fenêtre précédente**|Le handle de la fenêtre de frère précédent dans le même ordre (Z-order) indiqué dans l’arborescence de fenêtre (« none », s’il n’existe aucune fenêtre précédente). Choisissez cette entrée pour afficher les propriétés de la fenêtre précédente.|  
|**Fenêtre parente**|Handle de cette fenêtre parente (« none », s’il n’existe aucun parent). Choisissez cette entrée pour afficher les propriétés de la fenêtre parente.|  
|**Premier enfant**|Handle de première fenêtre enfant cette fenêtre, dans la séquence (Z-order) indiqué dans l’arborescence de fenêtre (« none », si aucune fenêtre enfant). Choisissez cette valeur pour afficher les propriétés de la première fenêtre enfant.|  
|**Fenêtre propriétaire**|Le handle de fenêtre de propriétaire de cette fenêtre. Fenêtre principale d’une application possède généralement des fenêtres de boîte de dialogue modale du système, par exemple (« none », s’il n’existe aucun propriétaire). Choisissez cette entrée pour afficher les propriétés de la fenêtre propriétaire.|