---
title: Migrer des analyseurs FxCop vers les analyseurs .NET
ms.custom: SEO-VS-2020
description: Découvrez comment migrer des analyseurs FxCop vers des analyseurs .NET
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
ms.openlocfilehash: d6f9c36b1b64abe648c3aa9014c633e4e4949b1a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798256"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Migrer des analyseurs FxCop vers les analyseurs .NET

Les analyseurs de la source par .NET Compiler Platform (« Roslyn ») remplacent l' [analyse héritée](code-analysis-for-managed-code-overview.md) du code managé. La plupart des règles d’analyse héritée (FxCop) ont déjà été réécrites en tant qu’analyseurs sources.

Avant Visual Studio 2019 16,8 et .NET 5,0, ces analyseurs étaient fournis sous forme de `Microsoft.CodeAnalysis.FxCopAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

À compter de Visual Studio 2019 16,8 et .NET 5,0, ces analyseurs sont [inclus dans le kit de développement logiciel (SDK) .net](/dotnet/fundamentals/code-analysis/overview). Si vous ne souhaitez pas migrer vers le kit de développement logiciel (SDK) .NET 5 + ou si vous préférez un modèle basé sur un package NuGet, les analyseurs sont également disponibles dans le `Microsoft.CodeAnalysis.NetAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Vous préférerez peut-être un modèle basé sur des packages pour les mises à jour de version à la demande.

> [!NOTE]
> Les analyseurs .NET de premier tiers sont indépendants de la plateforme cible. Autrement dit, votre projet n’a pas besoin de cibler une plateforme .NET spécifique. Les analyseurs fonctionnent pour les projets qui ciblent ainsi que les `net5.0` versions antérieures de .net, telles que `netcoreapp` , `netstandard` et `net472` .

## <a name="migration-steps"></a>Étapes de la migration

À partir de la version `3.3.2` , le `Microsoft.CodeAnalysis.FxCopAnalyzers` package NuGet est déconseillé. Suivez les étapes ci-dessous pour migrer votre projet ou votre solution de `Microsoft.CodeAnalysis.FxCopAnalyzers` vers les analyseurs .net :

1. Désinstaller le `Microsoft.CodeAnalysis.FxCopAnalyzers` package NuGet

2. [Activez ou installez les analyseurs .net](install-net-analyzers.md). Notez que vous n’avez pas besoin de modifier la plateforme cible de votre projet.

3. Activer des règles supplémentaires : `Microsoft.CodeAnalysis.NetAnalyzers` est bien plus prudent par rapport à `Microsoft.CodeAnalysis.FxCopAnalyzers` . Contrairement au package FxCopAnalyzers, il n’y a que quelques règles de vérification qui sont [activées par défaut en tant qu’avertissements de génération](/dotnet/fundamentals/code-analysis/overview#enabled-rules). Vous pouvez [activer des règles supplémentaires](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) en personnalisant la propriété MSBuild [AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) . Par exemple, la définition de la propriété sur permet d' `AllEnabledByDefault` activer toutes les règles d’autorité de certification applicables comme avertissements de génération par défaut.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Voir aussi

- [Analyse du code source et analyse héritée](net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)
- [Migrer d’une analyse existante vers les analyseurs .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Activer ou installer les analyseurs .NET](install-net-analyzers.md)
- [FAQ sur les analyseurs .NET](net-analyzers-faq.yml)
- [Configurer les analyseurs .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
