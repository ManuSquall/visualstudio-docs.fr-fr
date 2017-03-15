---
title: "MSBuild Error MSB3143 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CopyPackageError"
helpviewer_keywords: 
  - "MSB3143"
ms.assetid: b4278c8c-31df-4b4f-9ef9-7b9327e8ee77
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3143
**MSB3143 : Une erreur s'est produite lors de la tentative de copie de '\<fichier\>' pour l'élément '\<package\>' : '\<erreur\>'**  
  
 Cette erreur se produit lorsque les packages de programme d'amorçage sont copiés vers le répertoire de sortie de génération.  Elle peut avoir plusieurs causes :  
  
-   Vous n'avez pas l'autorisation de copier vers le répertoire de sortie de génération.  
  
-   Le disque est saturé.  
  
 Ce sont les mêmes raisons potentielles qui expliquent l'échec de file.copy ou directory.createdirectory.  
  
## Voir aussi  
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)