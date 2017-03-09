---
title: "MSBuild Error MSB3164 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageHomeSiteMissing"
helpviewer_keywords: 
  - "MSB3164"
ms.assetid: 5a1e31fc-0322-4d4e-8c26-013b1efb82c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3164
**MSB3164 : Aucun attribut 'HomeSite' n'a été fourni pour '\<package\>'. Par conséquent, le package sera publié dans le même emplacement que le programme d'amorçage.**  
  
 Cet avertissement est généré lorsque l'utilisateur souhaite utiliser HomeSite, mais l'attribut HomeSite approprié pour le package spécifié n'est pas disponible.  
  
### Pour corriger cette erreur  
  
-   Mettez à jour les fichiers manifeste pour inclure l'attribut HomeSite.  
  
-   Ou n'utilisez pas HomeSite.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)