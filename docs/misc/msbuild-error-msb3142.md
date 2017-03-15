---
title: "MSBuild Error MSB3142 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.CopyError"
helpviewer_keywords: 
  - "MSB3142"
ms.assetid: acca7437-6c72-446c-a6b5-a1c051b6855f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3142
**MSB3142 : Une erreur s'est produite lors de la tentative de copie de '\<fichier\>' vers '\<dossier\>' : '\<erreur\>'**  
  
 Cette erreur est générée lors de la copie de setup.bin vers le répertoire de sortie de génération.  Elle peut avoir plusieurs causes :  
  
-   Vous n'avez pas l'autorisation de copier vers le répertoire de sortie.  
  
-   Le disque est saturé.  
  
 Ce sont les mêmes raisons potentielles qui expliquent l'échec de file.copy ou directory.createdirectory.  
  
## Voir aussi  
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)