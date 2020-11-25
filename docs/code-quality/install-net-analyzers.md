---
title: Activer ou installer les analyseurs .NET
ms.date: 08/03/2018
description: Découvrez comment activer les analyseurs .NET à partir du kit de développement logiciel (SDK) .NET ou installer ces analyseurs comme un package NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a14d89caba498a07c2447f9df1109e4da9f6a466
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112220"
---
# <a name="enable-or-install-net-analyzers"></a>Activer ou installer les analyseurs .NET

## <a name="overview"></a>Vue d’ensemble

Les analyseurs .NET Compiler Platform (Roslyn) inspectent la qualité et les problèmes de styles de code de votre code C# ou Visual Basic. Vous pouvez activer ou installer ces analyseurs de l’une des manières suivantes :

- **Activation à partir du kit de développement logiciel (SDK) .net**: à compter de Visual Studio 2019 16,8 et .net 5,0, ces analyseurs sont [inclus dans le kit de développement logiciel (SDK) .net](/dotnet/fundamentals/code-analysis/overview). L’analyse est activée par défaut pour les projets qui ciblent .NET 5,0 ou une version ultérieure. Vous pouvez activer l’analyse du code sur des projets qui ciblent des versions antérieures de .NET en affectant à la propriété la valeur `EnableNETAnalyzers` `true` . Vous pouvez également désactiver l’analyse du code pour votre projet en affectant à la valeur `EnableNETAnalyzers` `false` .

- **Installer en tant que package NuGet**: vous pouvez également installer ces analyseurs en installant le `Microsoft.CodeAnalysis.NetAnalyzers` [package nuget](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) sur Visual Studio 2019. Si vous utilisez Visual Studio 2017, installez la dernière `2.9.x` version du `Microsoft.CodeAnalysis.FxCopAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/).

> [!NOTE]
> Il est recommandé d’activer les analyseurs à partir du kit de développement logiciel (SDK) .NET au lieu d’installer le `Microsoft.CodeAnalysis.NetAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), dans la mesure du possible. L’activation des analyseurs à partir du kit de développement logiciel (SDK) .NET garantit que vous recevez automatiquement les correctifs de bogue de l’analyseur et de nouveaux analyseurs dès que vous mettez à jour le kit de développement logiciel.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de code dans Visual Studio](roslyn-analyzers-overview.md)
- [Utiliser des analyseurs de code dans Visual Studio](use-roslyn-analyzers.md)
- [Migrer de l’analyse héritée vers les analyseurs .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Migrer des analyseurs FxCop vers des analyseurs .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
