---
title: "Onglet Général, boîte de dialogue Propriétés de fenêtre | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b26896ce119e49ec2d001a0b09bc7b563bd7cac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="general-tab-window-properties-dialog-box"></a>Onglet Général de la boîte de dialogue Propriétés de la fenêtre
Utilisez le **général** onglet pour afficher plus d’informations sur la fenêtre sélectionnée. Pour afficher le [boîte de dialogue Propriétés de fenêtre](../debugger/window-properties-dialog-box.md), déplacer le focus vers le [affichage Windows](../debugger/windows-view.md) fenêtre. Sélectionnez n’importe quel nœud de fenêtre dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **général** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Légende de fenêtre**|Le texte dans la légende de fenêtre, ou le texte contenu dans une fenêtre s’il s’agit d’un contrôle.|  
|**Handle de fenêtre**|ID unique de cette fenêtre. Les numéros de handle de fenêtre sont réutilisés ; ils identifient une fenêtre uniquement pour la durée de vie de cette fenêtre.|  
|**Procédure de fenêtre**|L’adresse virtuelle de la fonction de procédure de fenêtre pour cette fenêtre. Ce champ indique également si cette fenêtre est une fenêtre Unicode et si elle est sous-classée.|  
|**Rectangle**|Le rectangle englobant de la fenêtre. La taille du rectangle s’affiche également. Les unités sont les pixels en coordonnées d’écran.|  
|**Rectangle restauré**|Le rectangle englobant de la fenêtre restaurée. La taille du rectangle s’affiche également. Rectangle restauré diffère de Rectangle uniquement lorsque la fenêtre est agrandie ou réduite. Les unités sont les pixels en coordonnées d’écran.|  
|**Rect du client**|Le rectangle englobant pour la zone cliente de fenêtre. La taille du rectangle s’affiche également. Les unités sont les pixels par rapport au coin supérieur gauche de la zone cliente de fenêtre.|  
|**Handle d’instance**|Le handle d’instance de l’application. Handles d’instance ne sont pas uniques.|  
|**ID de contrôle ou Handle de Menu**|Si la fenêtre affichée est une fenêtre enfant, l’étiquette de l’ID de contrôle s’affiche. ID de contrôle est un entier qui identifie l’ID du contrôle. de cette fenêtre enfant Si la fenêtre affichée n’est pas une fenêtre enfant, l’étiquette du Handle de Menu s’affiche. Handle de menu est un entier qui identifie le handle du menu associé à cette fenêtre.|  
|**Données utilisateur**|Données spécifiques à l’application qui sont attachées à cette structure de fenêtre.|  
|**Octets de la fenêtre**|Nombre d’octets supplémentaires associés à cette fenêtre. La signification de ces octets est déterminée par l’application. Développez la zone de liste pour afficher les valeurs d’octets au format DWORD.|