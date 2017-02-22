---
title: "Op&#233;rateurs logiques dans les expressions de recherche | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Help Viewer 2.0, opérateurs logiques dans la recherche"
  - "opérateurs logiques dans la recherche [Help Viewer 2.0]"
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Op&#233;rateurs logiques dans les expressions de recherche
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En utilisant des opérateurs logiques, vous pouvez affiner votre recherche de contenu en créant des expressions de recherche plus complexes à partir d'expressions de recherche simples.  Comme le montre le tableau suivant, les opérateurs logiques spécifient comment plusieurs termes de recherche doivent être combinés dans une requête de recherche.  
  
> [!IMPORTANT]
>  Vous devez entrer les opérateurs logiques en majuscules pour que le moteur de recherche les identifie.  
  
|Pour rechercher|Utilisation|Exemple|Résultat|  
|---------------------|-----------------|-------------|--------------|  
|Les deux termes dans la même rubrique|AND|dib AND palette|Rubriques qui contiennent « dib » et « palette ».|  
|L'un ou l'autre des termes dans une rubrique|OR|raster OR vecteur|Rubriques qui contiennent « raster » OR « vecteur ».|  
|Premier terme sans le second terme dans la même rubrique|NOT|« système d'exploitation » NOT « DOS »|Rubriques qui contiennent « système d'exploitation » NOT « DOS ».|  
|Les deux termes, voisins dans une rubrique|NEAR|utilisateur NEAR noyau|Rubriques qui contiennent « utilisateur » à proximité directe de « noyau ».|  
  
## Voir aussi  
 [Conseils de recherche en texte intégral](../ide/full-text-search-tips.md)   
 [Informations relatives aux paramètres régionaux](../ide/locate-information.md)