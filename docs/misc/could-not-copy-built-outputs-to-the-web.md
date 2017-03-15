---
title: "Impossible de copier les sorties de la build sur le web | Microsoft Docs"
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
  - "vs.tasklisterror.cantcopyoutputstoweb"
ms.assetid: 59cf714b-cf7d-4df9-81ae-d3254969d5bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Impossible de copier les sorties de la build sur le web
Le système de projet n’a pas pu copier un ou plusieurs fichiers de sortie de la build \(par exemple, la DLL, le fichier PDB ou des assemblys satellites\) sur le serveur web.  
  
 Cette erreur indique qu’un ou plusieurs fichiers de sortie de la build n’ont pas été copiés sur le serveur web.  
  
 Elle se produit généralement si un fichier de sortie de la build est verrouillé ou en lecture seule sur le serveur. Si un fichier est verrouillé sur le serveur, cela indique que le runtime [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n’a pas copié correctement les assemblys, les satellites ou les symboles de débogage qui sont actuellement sur le serveur.  
  
 Cela peut également indiquer que le serveur ne dispose pas assez d’espace disque ou que des problèmes réseau empêchent [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de charger les fichiers sur le web.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l’espace disque disponible.  
  
2.  Si un ou plusieurs fichiers sont verrouillés, redémarrez le serveur web pour libérer le verrou [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mis sur ces fichiers.  
  
## Voir aussi  
 [PDB Files](http://msdn.microsoft.com/fr-fr/1761c84e-8c2c-4632-9649-b5f99964ed3f)