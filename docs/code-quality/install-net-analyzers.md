---
title: Activer ou installer des analyseurs .NET internes
ms.date: 08/03/2018
description: Découvrez comment activer des analyseurs .NET de premier tiers à partir du kit de développement logiciel (SDK) .NET ou installer ces analyseurs comme un package NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: b41615e1826987cb42076ab3195fe7bfad235e7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867891"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Activer ou installer des analyseurs .NET internes

## <a name="overview"></a>Vue d’ensemble

Les analyseurs .NET Compiler Platform (Roslyn) inspectent la qualité et les problèmes de styles de code de votre code C# ou Visual Basic. Les analyseurs .NET de premier tiers sont **indépendants de la plateforme cible**. Autrement dit, votre projet n’a pas besoin de cibler une plateforme .NET spécifique. Les analyseurs fonctionnent pour les projets qui ciblent ainsi que les `net5.0` versions antérieures de .net, telles que `netcoreapp` , `netstandard` et `net472` .

Vous pouvez activer ou installer les analyseurs .NET du premier groupe de l’une des manières suivantes :

- **Activation à partir du kit de développement logiciel (SDK) .net**: à compter de Visual Studio 2019 16,8 et .net 5,0, ces analyseurs sont [inclus dans le kit de développement logiciel (SDK) .net](/dotnet/fundamentals/code-analysis/overview). L’analyse est activée par défaut pour les projets qui ciblent .NET 5,0 ou une version ultérieure. Vous pouvez activer l’analyse du code sur des projets qui ciblent des versions antérieures de .NET en affectant à la propriété la valeur `EnableNETAnalyzers` `true` . Vous pouvez également désactiver l’analyse du code pour votre projet en affectant à la valeur `EnableNETAnalyzers` `false` .

- **Installer en tant que package NuGet**: Si vous ne souhaitez pas passer au kit de développement logiciel (SDK) .net 5 + ou si vous préférez un modèle basé sur un package NuGet, les analyseurs sont également disponibles dans le `Microsoft.CodeAnalysis.NetAnalyzers` [package nuget](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) sur Visual Studio 2019.  Vous préférerez peut-être un modèle basé sur des packages pour les mises à jour de version à la demande. Si vous utilisez Visual Studio 2017, installez la dernière `2.9.x` version du `Microsoft.CodeAnalysis.FxCopAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) à la place.

> [!NOTE]
> Il est recommandé d’activer les analyseurs à partir du kit de développement logiciel (SDK) .NET au lieu d’installer le `Microsoft.CodeAnalysis.NetAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), dans la mesure du possible. L’activation des analyseurs à partir du kit de développement logiciel (SDK) .NET garantit que vous recevez automatiquement les correctifs de bogue de l’analyseur et de nouveaux analyseurs dès que vous mettez à jour le kit de développement logiciel. Dans le modèle NuGet, vous devez mettre à jour le package NuGet chaque fois que vous souhaitez les correctifs de bogues les plus récents. Le package NuGet est mis à jour plus fréquemment.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de code dans Visual Studio](roslyn-analyzers-overview.md)
- [Utiliser des analyseurs de code dans Visual Studio](use-roslyn-analyzers.md)
- [Migrer d’une analyse existante vers les analyseurs .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Migrer des analyseurs FxCop vers les analyseurs .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
