---
title: Classe, onglet de boîte de dialogue Propriétés de fenêtre | Microsoft Docs
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
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6eba6a12714c1b4f58ae9d6bb17f696c3c452411
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749327"
---
# <a name="class-tab-window-properties-dialog-box"></a>Onglet Classe de la boîte de dialogue Propriétés de la fenêtre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilisez le **classe** onglet pour afficher des informations sur la classe de la fenêtre sélectionnée. Pour afficher le [boîte de dialogue Propriétés de fenêtre](../debugger/window-properties-dialog-box.md), déplacer le focus vers le [Windows vue](../debugger/windows-view.md) fenêtre. Sélectionnez n’importe quel nœud de fenêtre dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **classe** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Nom de classe**|Nom (ou nombre ordinal) de cette classe de fenêtre.|  
|**Styles de classe**|Une combinaison des codes de style de classe.|  
|**Octets de la classe**|Données spécifiques à l’application associées à cette classe de fenêtre.|  
|**Classe Atom**|Atome de la classe retournée par la **RegisterClass** appeler.|  
|**Handle d’instance**|Le handle d’instance du module qui inscrit la classe. Handles d’instance ne sont pas uniques.|  
|**Octets de la fenêtre**|Nombre d’octets supplémentaires associés à chaque fenêtre de cette classe. La signification de ces octets est déterminée par l’application. Développez la zone de liste pour afficher les valeurs d’octets au format DWORD.|  
|**Procédure de fenêtre**|L’adresse actuelle de la **WndProc** (fonction) pour windows de cette classe. Cela diffère de **fenêtre Proc** sur le **général** onglet si la fenêtre est une sous-classe.|  
|**Nom de menu**|Le nom du menu principal qui est associé à windows de cette classe (« none », s’il n’existe aucun menu).|  
|**Handle de l’icône**|Le handle de l’icône associée à windows de cette classe (« none », s’il n’existe aucune icône).|  
|**Handle de curseur**|Le handle du curseur associé à windows de cette classe (« none », s’il n’existe aucun curseur).|  
|**Pinceau d’arrière-plan**|Le handle pour le pinceau d’arrière-plan qui est associé à windows de cette classe, ou une des couleurs COLOR_ * pour peindre l’arrière-plan de fenêtre (« none », s’il n’existe aucun pinceau).|



