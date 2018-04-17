---
title: Classe, onglet de boîte de dialogue Propriétés de fenêtre | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 573eb3f9cbcaedddc67524e81b2508df2112de04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="class-tab-window-properties-dialog-box"></a>Onglet Classe de la boîte de dialogue Propriétés de la fenêtre
Utilisez le **classe** onglet pour afficher des informations sur la classe de la fenêtre sélectionnée. Pour afficher le [boîte de dialogue Propriétés de fenêtre](../debugger/window-properties-dialog-box.md), déplacer le focus vers le [affichage Windows](../debugger/windows-view.md) fenêtre. Sélectionnez n’importe quel nœud de fenêtre dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.  
  
 Les paramètres suivants sont disponibles sur le **classe** onglet :  
  
|Entrée|Description|  
|-----------|-----------------|  
|**Nom de classe**|Nom (ou nombre ordinal) de cette classe de fenêtre.|  
|**Styles de classe**|Combinaison de codes de style de classe.|  
|**Octets de la classe**|Données spécifiques à l’application associées à cette classe de fenêtre.|  
|**Classe Atom**|Atome de la classe retournée par le **RegisterClass** appeler.|  
|**Handle d’instance**|Le handle d’instance du module qui inscrit la classe. Handles d’instance ne sont pas uniques.|  
|**Octets de la fenêtre**|Nombre d’octets supplémentaires associés à chaque fenêtre de cette classe. La signification de ces octets est déterminée par l’application. Développez la zone de liste pour afficher les valeurs d’octets au format DWORD.|  
|**Procédure de fenêtre**|L’adresse actuelle de la **WndProc** fonction pour les fenêtres de cette classe. Cela diffère de **procédure de fenêtre** sur la **général** onglet si la fenêtre est sous-classée.|  
|**Nom de menu**|Le nom du menu principal qui est associé aux fenêtres de cette classe (« aucun », s’il n’existe aucun menu).|  
|**Handle de l’icône**|Le handle de l’icône qui est associé aux fenêtres de cette classe (« aucun », s’il n’existe aucune icône).|  
|**Handle de curseur**|Le handle du curseur qui est associé aux fenêtres de cette classe (« aucun », s’il n’existe aucun curseur).|  
|**Pinceau d’arrière-plan**|Le handle du pinceau d’arrière-plan qui est associé aux fenêtres de cette classe, ou une des couleurs COLOR_ * pour peindre l’arrière-plan de fenêtre (« aucun », s’il n’existe aucun pinceau).|