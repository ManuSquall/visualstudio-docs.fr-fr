---
title: Utilisation efficace de la mémoire lors de la génération de projets volumineux | Microsoft Docs
description: Découvrez comment MSBuild gère automatiquement la mémoire, comme le déchargement de versions antérieures et la récupération de caches, lors de la création de projets volumineux.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99cee9cfbf779bbee97c00fb76f9670e1d609b00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965900"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Utilisation efficace de la mémoire lors de la génération de projets volumineux

Les projets volumineux contiennent souvent de nombreux sous-projets et autres dépendances, qui peuvent consommer beaucoup de mémoire système au moment de la génération. Lorsque la mémoire système disponible diminue, les performances du système peuvent elles aussi diminuer. Les versions antérieures des projets MSBuild sont restées en mémoire. La version 3.5 a supprimé des versions antérieures des projets, mais conservé les résultats de build dans un cache pour une récupération ultérieure.

 La version 4.0 gère cette mémoire automatiquement, ce qui évite aux projets d’avoir à utiliser des propriétés telles que `UnloadProjectsOnCompletion` et `UseResultsCache`.

### <a name="see-also"></a>Voir aussi

- [Générer plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
