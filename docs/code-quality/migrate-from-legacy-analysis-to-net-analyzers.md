---
title: Migrer de FxCop vers la source Analysis (analyseurs .NET)
ms.custom: SEO-VS-2020
description: Découvrez comment analyser du code pour la première fois ou comment effectuer une migration à partir de l’analyse binaire (FxCop) vers la nouvelle méthode d’analyse du code managé à l’aide de l’analyse de la source (analyseurs .NET).
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 9a673e7467816e71b8240de9e5f68840c9188dcd
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798230"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Migrer de l’analyse héritée (FxCop) vers l’analyse source (analyseurs .NET)

Les analyseurs de la source par .NET Compiler Platform (« Roslyn ») remplacent l' [analyse héritée](../code-quality/code-analysis-for-managed-code-overview.md) du code managé. Pour les modèles de projet plus récents tels que les projets .NET Core et .NET Standard, l’analyse héritée n’est pas disponible.

La plupart des règles d’analyse héritée (FxCop) ont déjà été réécrites pour les analyseurs .NET, un ensemble d’analyseurs de code Roslyn. Les analyseurs Roslyn exécutent une analyse basée sur le code source lors de l’exécution du compilateur. Les résultats des analyseurs sont signalés en même temps que les résultats du compilateur.

Pour plus d’informations sur les différences entre l’analyse héritée et l’analyse de la source, consultez les rubriques suivantes :

- [Analyse du code source et analyse héritée](../code-quality/net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)

- [FAQ sur les analyseurs .NET](../code-quality/net-analyzers-faq.yml)

## <a name="migration"></a>Migration

Pour migrer vers l’analyse de la source, [activez ou installez les analyseurs .net](install-net-analyzers.md). À l’instar des violations des règles d’analyse héritées, les violations de l’analyse du code source s’affichent dans la fenêtre Liste d’erreurs dans Visual Studio. En outre, les violations de l’analyse du code source s’affichent également dans l’éditeur de code sous forme de *tildes* sous le code incriminé. La couleur de la ligne ondulée dépend du [paramètre de gravité](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) de la règle. Pour afficher l’état des règles portées vers les nouveaux analyseurs .NET, consultez [règles portées et](../code-quality/fxcop-rule-port-status.md)déplacées.

> [!NOTE]
> Avant Visual Studio 2019 16,8 et .NET 5,0, ces analyseurs étaient fournis sous forme de `Microsoft.CodeAnalysis.FxCopAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). À compter de Visual Studio 2019 16,8 et .NET 5,0, ces analyseurs sont [inclus dans le kit de développement logiciel (SDK) .net](/dotnet/fundamentals/code-analysis/overview). Ils sont également disponibles en tant que `Microsoft.CodeAnalysis.NetAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Pour plus d’informations, consultez [migrer des analyseurs FxCop vers les analyseurs .net](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="configuration"></a>Configuration

Pour en savoir plus sur la configuration des analyseurs .NET :

- Pour configurer les analyseurs .NET, consultez [configurer les analyseurs .net](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Pour en savoir plus sur la configuration des analyseurs à l’aide de règles prédéfinies avec EditorConfig ou un fichier d’ensemble de règles, consultez [activer une catégorie de règles](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

## <a name="see-also"></a>Voir aussi

- [Migrer des analyseurs FxCop vers les analyseurs .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
