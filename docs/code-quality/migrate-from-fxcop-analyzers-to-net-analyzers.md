---
title: Migrer des analyseurs FxCop vers des analyseurs .NET
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
manager: jillfra
ms.openlocfilehash: b62f99b296c0f9624079423d850029f804e5ebe4
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112228"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Migrer des analyseurs FxCop vers des analyseurs .NET

Les analyseurs de la source par .NET Compiler Platform (« Roslyn ») remplacent l' [analyse héritée](code-analysis-for-managed-code-overview.md) du code managé. La plupart des règles d’analyse héritée (FxCop) ont déjà été réécrites en tant qu’analyseurs sources.

Avant Visual Studio 2019 16,8 et .NET 5,0, ces analyseurs étaient fournis sous forme de `Microsoft.CodeAnalysis.FxCopAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

À compter de Visual Studio 2019 16,8 et .NET 5,0, ces analyseurs sont [inclus dans le kit de développement logiciel (SDK) .net](/dotnet/fundamentals/code-analysis/overview). Ils sont également disponibles en tant que `Microsoft.CodeAnalysis.NetAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). `Microsoft.CodeAnalysis.FxCopAnalyzers` Le package NuGet sera bientôt déconseillé.

## <a name="migration-steps"></a>Étapes de la migration

Suivez les étapes ci-dessous pour migrer votre projet ou votre solution de `Microsoft.CodeAnalysis.FxCopAnalyzers` vers les analyseurs .net :

1. Désinstaller le `Microsoft.CodeAnalysis.FxCopAnalyzers` package NuGet

2. [Activer ou installer les analyseurs .NET](install-net-analyzers.md)

3. Activer des règles supplémentaires : `Microsoft.CodeAnalysis.NetAnalyzers` est bien plus prudent par rapport à `Microsoft.CodeAnalysis.FxCopAnalyzers` . Contrairement au package FxCopAnalyzers, il n’y a que quelques règles de vérification qui sont [activées par défaut en tant qu’avertissements de génération](/dotnet/fundamentals/code-analysis/overview#enabled-rules). Vous pouvez [activer des règles supplémentaires](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) en personnalisant la propriété MSBuild [AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) . Par exemple, la définition de la propriété sur permet d' `AllEnabledByDefault` activer toutes les règles d’autorité de certification applicables comme avertissements de génération par défaut.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Voir aussi

- [Analyse du code source et analyse héritée](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Migrer de l’analyse héritée vers les analyseurs .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Activer ou installer les analyseurs .NET](install-net-analyzers.md)
- [FAQ sur les analyseurs .NET](net-analyzers-faq.md)
- [Configurer les analyseurs .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
