---
title: "Onglet Classe de la bo&#238;te de dialogue Propri&#233;t&#233;s de la fen&#234;tre | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Propriétés de la fenêtre (boîte de dialogue), Onglet Classe"
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Onglet Classe de la bo&#238;te de dialogue Propri&#233;t&#233;s de la fen&#234;tre
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez l'onglet **Classe** pour afficher des informations sur la classe de la fenêtre sélectionnée.  Pour afficher la [boîte de dialogue Propriétés de la fenêtre](../debugger/window-properties-dialog-box.md), déplacez le focus sur la fenêtre [Vue Fenêtres](../debugger/windows-view.md).  Sélectionnez n'importe quel nœud de fenêtre dans l'arborescence, puis sélectionnez **Propriétés** dans le menu **Affichage**.  
  
 Les paramètres suivants sont disponibles sous l'onglet **Classe** :  
  
|Entry|Description|  
|-----------|-----------------|  
|**Nom de la classe**|Nom \(ou numéro ordinal\) de cette classe de fenêtre.|  
|**Styles de la classe**|Combinaison des codes de style de classe.|  
|**Octets de la classe**|Données spécifiques à l'application associées à cette classe de fenêtre.|  
|**Classe Atom**|Atome de la classe retournée par l'appel de **RegisterClass**.|  
|**Handle d'instance**|Handle d'instance du module qui a inscrit la classe.  Les handles d'instances ne sont pas uniques.|  
|**Octets de la fenêtre**|Nombre d'octets supplémentaires associés à chaque fenêtre de cette classe.  La signification de ces octets est déterminée par l'application.  Développez la zone de liste pour voir les valeurs d'octets au format DWORD.|  
|**Proc. de la fenêtre**|Adresse actuelle de la fonction **WndProc** pour les fenêtres de cette classe.  Cela est différent de **Proc. de la fenêtre** sous l'onglet **Général** si la fenêtre est sous\-classée.|  
|**Nom de menu**|Nom du menu principal associé aux fenêtres de cette classe \("aucun", s'il n'y a aucun menu\).|  
|**Handle de l'icône**|Handle de l'icône associée aux fenêtres de cette classe \("aucun", s'il n'y a aucune icône\).|  
|**Handle du curseur**|Handle du curseur associé aux fenêtres de cette classe \("aucun", s'il n'y a aucun curseur\).|  
|**Pinceau d'arrière\-plan**|Handle du pinceau d'arrière\-plan associé aux fenêtres de cette classe, ou une des couleurs COLOR\_\* prédéfinies pour peindre l'arrière\-plan des fenêtres \("aucun", s'il n'y a aucun pinceau\).|