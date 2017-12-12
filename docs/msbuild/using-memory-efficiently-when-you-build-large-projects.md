---
title: "Utilisation efficace de la mémoire lors de la génération de projets volumineux | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: e9484e0b8771ad665f1891298ff2f6a8a1d0005e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Utilisation efficace de la mémoire lors de la génération de projets volumineux
Les projets volumineux contiennent souvent de nombreux sous-projets et autres dépendances, qui peuvent consommer beaucoup de mémoire système au moment de la génération. Lorsque la mémoire système disponible diminue, les performances du système peuvent elles aussi diminuer. Les versions antérieures des projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] restaient en mémoire. Dans la version 3.5, les projets étaient supprimés, mais les résultats de la génération étaient conservés dans un cache pour pouvoir être récupérés par la suite.  
  
 La version 4.0 gère cette mémoire automatiquement, ce qui évite aux projets d’avoir à utiliser des propriétés telles que `UnloadProjectsOnCompletion` et `UseResultsCache`.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération parallèle de plusieurs projets](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)