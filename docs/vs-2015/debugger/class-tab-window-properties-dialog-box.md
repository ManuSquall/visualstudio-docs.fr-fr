---
title: Onglet classe de la boîte de dialogue Propriétés de la fenêtre | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7f81a100b2c2311444732434df0f5c5599742a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161609"
---
# <a name="class-tab-window-properties-dialog-box"></a>Onglet Classe de la boîte de dialogue Propriétés de la fenêtre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilisez l’onglet **classe** pour afficher des informations sur la classe de la fenêtre sélectionnée. Pour afficher la [boîte de dialogue Propriétés](../debugger/window-properties-dialog-box.md)de la fenêtre, déplacez le focus vers la fenêtre [vue Windows](../debugger/windows-view.md) . Sélectionnez un nœud de fenêtre dans l’arborescence, puis choisissez **Propriétés** dans le menu **affichage** .  
  
 Les paramètres suivants sont disponibles sous l’onglet **classe** :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Nom de la classe**|Nom (ou numéro ordinal) de cette classe de fenêtre.|  
|**Styles de la classe**|Combinaison de codes de style de classe.|  
|**Octets de la classe**|Données spécifiques à l’application associées à cette classe de fenêtre.|  
|**Classe Atom**|Atom pour la classe retournée par l’appel **registerClass** .|  
|**Handle d’instance**|Handle d’instance du module qui a inscrit la classe. Les handles d’instance ne sont pas uniques.|  
|**Octets de la fenêtre**|Nombre d’octets supplémentaires associés à chaque fenêtre de cette classe. La signification de ces octets est déterminée par l’application. Développez la zone de liste pour afficher les valeurs d’octets au format DWORD.|  
|**Proc. de la fenêtre**|Adresse actuelle de la fonction **WndProc** pour les fenêtres de cette classe. Cela diffère de la **procédure de fenêtre** sous l’onglet **général** si la fenêtre est sous-classée.|  
|**Nom de menu**|Nom du menu principal associé aux fenêtres de cette classe (« None » s’il n’y a aucun menu).|  
|**Handle de l’icône**|Handle de l’icône associée aux fenêtres de cette classe ("none" s’il n’y a pas d’icône).|  
|**Handle du curseur**|Handle du curseur associé aux fenêtres de cette classe ("none" s’il n’y a aucun curseur).|  
|**Pinceau d’arrière-plan**|Handle pour le pinceau d’arrière-plan associé aux fenêtres de cette classe, ou l’une des couleurs prédéfinies COLOR_ * pour peindre l’arrière-plan de la fenêtre (« aucun » s’il n’y a aucun pinceau).|
