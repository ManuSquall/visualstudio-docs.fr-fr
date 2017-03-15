---
title: "Unable to retrieve resource information | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_scan_failed"
ms.assetid: e4389ff0-eb64-4c31-b32f-5216c73fadfb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to retrieve resource information
L'analyse de la hiérarchie des fichiers .resx a échoué.  
  
 Dans le cadre de l'étape de build `Preparing resources`, qui s'affiche dans la fenêtre **Sortie**, le système de projet analyse la hiérarchie du projet pour tous les fichiers ayant une extension .resx.  Il en résulte une liste de fichiers XML .resx qui doivent être transformés en fichiers binaires .resources avant de pouvoir être inclus en tant que ressources dans la sortie de projet.  
  
 **Pour corriger cette erreur**  
  
-   Redémarrez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si cela ne fonctionne pas, appelez les Services de Support technique de Microsoft pour signaler le problème.  
  
     Cette erreur entraîne l'échec de la génération.  
  
## Voir aussi  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/fr-fr/f793852c-da06-4d52-a826-65f635844772)