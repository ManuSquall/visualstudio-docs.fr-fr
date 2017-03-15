---
title: "MSBuild Error MSB3187 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.PlatformMismatch"
helpviewer_keywords: 
  - "MSB3187"
ms.assetid: c5e93c14-b099-4176-bf1b-dbecc47fb3fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3187
**MSB3187 : L'assembly référencé  '\<assembly\>'  cible un processeur différent de l'application.**  
  
 Cet avertissement est généré lorsque la plateforme cible de l'application \(architecture du processeur\) a une valeur neutre \(MSIL\) et l'assembly référencé n'est pas neutre, ou si l'architecture de l'application n'est pas neutre et la dépendance est neutre.  De même, si la plateforme des deux éléments n'est pas neutre, leur architecture doit correspondre.  En outre, l'architecture de l'application et l'architecture de l'assembly du point d'entrée doivent toujours correspondre.  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que la plateforme cible de l'application \(architecture du processeur\) corresponde à tous les assemblys référencés et à l'architecture de l'assembly du point d'entrée.  
  
## Voir aussi  
 [Paramètres avancés du compilateur, boîte de dialogue \(Visual Basic\)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)   
 [Générer, page du Concepteur de projets \(C\#\)](../ide/reference/build-page-project-designer-csharp.md)