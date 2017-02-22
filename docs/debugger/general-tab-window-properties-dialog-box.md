---
title: "Onglet G&#233;n&#233;ral de la bo&#238;te de dialogue Propri&#233;t&#233;s de la fen&#234;tre | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Propriétés de la fenêtre (boîte de dialogue), onglet Général"
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Onglet G&#233;n&#233;ral de la bo&#238;te de dialogue Propri&#233;t&#233;s de la fen&#234;tre
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez l'onglet **Général** pour afficher les informations relatives à la fenêtre sélectionnée.  Pour afficher la [boîte de dialogue Propriétés de la fenêtre](../debugger/window-properties-dialog-box.md), déplacez le focus sur la fenêtre [Vue Fenêtres](../debugger/windows-view.md).  Sélectionnez n'importe quel nœud de fenêtre dans l'arborescence, puis sélectionnez **Propriétés** dans le menu **Affichage**.  
  
 Les paramètres suivants sont disponibles sous l'onglet **Général** :  
  
|Entry|Description|  
|-----------|-----------------|  
|**Titre de la fenêtre**|Texte du titre de la fenêtre ou texte contenu dans une fenêtre, s'il s'agit d'un contrôle.|  
|**Handle de fenêtre**|ID unique de cette fenêtre.  Les numéros des handles de fenêtres sont réutilisés ; ils identifient une fenêtre uniquement pour la durée de vie de cette dernière.|  
|**Proc. de la fenêtre**|Adresse virtuelle de la fonction de la procédure de fenêtre pour cette fenêtre.  Ce champ indique également si cette fenêtre est une fenêtre Unicode, et si elle est sous\-classée.|  
|**Rectangle**|Rectangle englobant de la fenêtre.  La taille du rectangle est également affichée.  Les unités sont des pixels en coordonnées d'écran.|  
|**Rectangle restauré**|Rectangle englobant de la fenêtre restaurée.  La taille du rectangle est également affichée.  Rectangle restauré diffère de Rectangle uniquement lorsque la fenêtre est agrandie ou réduite.  Les unités sont des pixels en coordonnées d'écran.|  
|**Rectangle client**|Rectangle englobant de la zone cliente de la fenêtre.  La taille du rectangle est également affichée.  Les unités sont exprimées en pixels par rapport au bord supérieur gauche de la zone cliente de la fenêtre.|  
|**Handle d'instance**|Handle d'instance de l'application.  Les handles d'instances ne sont pas uniques.|  
|**ID du contrôle ou handle de menu**|Si la fenêtre affichée est une fenêtre enfant, l'étiquette de l'ID du contrôle est affichée.  L'ID du contrôle est un entier qui identifie l'ID du contrôle de cette fenêtre enfant.  Si la fenêtre affichée n'est pas une fenêtre enfant, l'étiquette du handle de menu est affichée.  Le handle de menu est un entier qui identifie le handle du menu associé à cette fenêtre.|  
|**Données utilisateur**|Données spécifiques à l'application, qui sont jointes à cette structure de fenêtre.|  
|**Octets de la fenêtre**|Nombre d'octets supplémentaires associés à cette fenêtre.  La signification de ces octets est déterminée par l'application.  Développez la zone de liste pour voir les valeurs d'octets au format DWORD.|