---
title: "Using Memory Efficiently When You Build Large Projects | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "memory use (MSBuild)"
  - "msbuild, efficient memory use building large trees"
  - "caching (MSBuild)"
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Using Memory Efficiently When You Build Large Projects
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les grands projets contiennent souvent de nombreux sous\-projets et d'autres dépendances, ceux\-ci peuvent consommer beaucoup de mémoire système au moment de la génération.  Lorsque la mémoire système disponible est réduite, les performances du système peuvent également être réduites.  Les versions antérieures des projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sont restées en mémoire ou, dans la version 3.5 les projets ont été supprimés, mais elle a conservé des résultats de build dans un cache en vue d'une récupération ultérieure.  
  
 La version 4.0 gère cette mémoire automatiquement, ce qui évite aux projets de devoir utiliser des propriétés telles que `UnloadProjectsOnCompletion` et `UseResultsCache`.  
  
## Voir aussi  
 [Building Multiple Projects in Parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)