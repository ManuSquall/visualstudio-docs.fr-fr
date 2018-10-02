---
title: Utilisation efficace de la mémoire lors de la génération de projets volumineux | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2cb204fcfb5a96fe9833571895513dfda4449b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503518"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Utilisation efficace de la mémoire lors de la génération de projets volumineux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [à l’aide de mémoire efficacement lorsque vous générez des projets volumineux](https://docs.microsoft.com/visualstudio/msbuild/using-memory-efficiently-when-you-build-large-projects).  
  
  
Les projets volumineux contiennent souvent de nombreux sous-projets et autres dépendances, qui peuvent consommer beaucoup de mémoire système au moment de la génération. Lorsque la mémoire système disponible diminue, les performances du système peuvent elles aussi diminuer. Les versions antérieures des projets [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] restaient en mémoire. Dans la version 3.5, les projets étaient supprimés, mais les résultats de la génération étaient conservés dans un cache pour pouvoir être récupérés par la suite.  
  
 La version 4.0 gère cette mémoire automatiquement, ce qui évite aux projets d’avoir à utiliser des propriétés telles que `UnloadProjectsOnCompletion` et `UseResultsCache`.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération parallèle de plusieurs projets](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)



