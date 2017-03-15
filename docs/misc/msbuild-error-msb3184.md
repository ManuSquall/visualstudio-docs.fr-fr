---
title: "MSBuild Error MSB3184 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidInputManifest"
helpviewer_keywords: 
  - "MSB3184"
ms.assetid: 2be9f8e9-04ee-4299-b79f-965ee57a1a34
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3184
**MSB3184 : Le manifeste d'entrée n'est pas valide.**  
  
 Cette erreur est générée lorsque le processus de génération tente de charger un fichier, en pensant qu'il contient un manifeste d'application ou de déploiement, alors qu'il renferme un autre élément \(par exemple, un autre manifeste ou des données altérées\).  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les manifestes contenus dans votre projet sont valides et appropriés.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)