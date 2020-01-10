---
title: Utilisation efficace de la mémoire lors de la génération de projets volumineux | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af61c15c8ef65c062c1aab6eba079c613f99b5f8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595226"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Utilisation efficace de la mémoire lors de la génération de projets volumineux
Les projets volumineux contiennent souvent de nombreux sous-projets et autres dépendances, qui peuvent consommer beaucoup de mémoire système au moment de la génération. Lorsque la mémoire système disponible diminue, les performances du système peuvent elles aussi diminuer. Les versions antérieures de projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] restaient en mémoire. La version 3.5 a supprimé des versions antérieures des projets, mais conservé les résultats de build dans un cache pour une récupération ultérieure.

 La version 4.0 gère cette mémoire automatiquement, ce qui évite aux projets d’avoir à utiliser des propriétés telles que `UnloadProjectsOnCompletion` et `UseResultsCache`.

### <a name="see-also"></a>Voir aussi
- [Générer plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
