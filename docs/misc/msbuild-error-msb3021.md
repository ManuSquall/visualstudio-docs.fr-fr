---
title: "MSBuild Error MSB3021 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Copy.Error"
helpviewer_keywords: 
  - "MSB3021"
ms.assetid: 8cb3a860-6916-4406-b5c7-b1106b44b92a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3021
**Impossible de copier le fichier "'\<fichier\>'" vers le fichier "'\<fichier\>'". '  \<erreur\>'**  
  
 La tâche `Copy` ne peut pas copier le fichier spécifié.  
  
### Pour corriger cette erreur  
  
-   Vérifiez si le fichier cible est verrouillé \(en cours d'utilisation\) par une autre application.  Assurez\-vous que vous êtes autorisé à lire le fichier source et à écrire le fichier cible dans le dossier cible.  Si le chemin d'accès de fichier de destination est extrêmement long, vous pouvez devoir copier vers un autre emplacement.  
  
## Voir aussi  
 [Copy Task](../msbuild/copy-task.md)   
 [Tasks](../msbuild/msbuild-tasks.md)