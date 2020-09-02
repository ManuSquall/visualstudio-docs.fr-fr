---
title: Onglet général de la boîte de dialogue Propriétés de la fenêtre | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b8733ef63a60baa1b268c42c8780cdf80f2674b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159962"
---
# <a name="general-tab-window-properties-dialog-box"></a>Onglet Général de la boîte de dialogue Propriétés de la fenêtre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilisez l’onglet **général** pour afficher des informations sur la fenêtre sélectionnée. Pour afficher la [boîte de dialogue Propriétés](../debugger/window-properties-dialog-box.md)de la fenêtre, déplacez le focus vers la fenêtre [vue Windows](../debugger/windows-view.md) . Sélectionnez un nœud de fenêtre dans l’arborescence, puis choisissez **Propriétés** dans le menu **affichage** .  
  
 Les paramètres suivants sont disponibles sous l’onglet **général** :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Titre de la fenêtre**|Texte dans le titre de la fenêtre ou texte contenu dans une fenêtre s’il s’agit d’un contrôle.|  
|**Handle de la fenêtre**|ID unique de cette fenêtre. Les numéros de handles de fenêtre sont réutilisés ; ils identifient une fenêtre uniquement pendant la durée de vie de cette fenêtre.|  
|**Proc. de la fenêtre**|Adresse virtuelle de la fonction de procédure de fenêtre pour cette fenêtre. Ce champ indique également si cette fenêtre est une fenêtre Unicode et si elle est sous-classée.|  
|**Rectangle**|Rectangle englobant pour la fenêtre. La taille du rectangle est également affichée. Les unités sont des pixels en coordonnées d’écran.|  
|**Rectangle restauré**|Rectangle englobant pour la fenêtre restaurée. La taille du rectangle est également affichée. Le Rect restauré est différent du rectangle uniquement lorsque la fenêtre est agrandie ou réduite. Les unités sont des pixels en coordonnées d’écran.|  
|**Rectangle client**|Rectangle englobant pour la zone cliente de la fenêtre. La taille du rectangle est également affichée. Les unités sont des pixels par rapport à l’angle supérieur gauche de la zone cliente de la fenêtre.|  
|**Handle d’instance**|Handle d’instance de l’application. Les handles d’instance ne sont pas uniques.|  
|**ID de contrôle ou descripteur de menu**|Si la fenêtre affichée est une fenêtre enfant, l’étiquette de l’ID de contrôle s’affiche. L’ID de contrôle est un entier qui identifie l’ID de contrôle de cette fenêtre enfant. Si la fenêtre affichée n’est pas une fenêtre enfant, l’étiquette du handle de menu s’affiche. Le descripteur de menu est un entier qui identifie la poignée du menu associé à cette fenêtre.|  
|**Données utilisateur**|Données spécifiques à l’application qui sont attachées à cette structure de fenêtre.|  
|**Octets de la fenêtre**|Nombre d’octets supplémentaires associés à cette fenêtre. La signification de ces octets est déterminée par l’application. Développez la zone de liste pour afficher les valeurs d’octets au format DWORD.|
