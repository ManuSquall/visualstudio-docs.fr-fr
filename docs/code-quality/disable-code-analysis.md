---
title: Désactiver l’analyse du code
ms.date: 09/01/2020
description: Découvrez comment désactiver l’analyse du code source Visual Studio dans les projets .NET Core, .NET Standard et .NET Framework.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.openlocfilehash: 6a1f1466caa921d46ce4701f5074b98f3d5ba051
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860384"
---
# <a name="disable-source-code-analysis-for-net"></a>Désactiver l’analyse du code source pour .NET

::: moniker range=">=vs-2019"

Cette page vous aide à désactiver l’analyse du code dans Visual Studio. Il existe des limitations quant à ce que vous pouvez désactiver, et la procédure de désactivation de l’analyse du code diffère selon plusieurs facteurs :

- Type de projet (.NET Core/standard et .NET Framework)

  Les projets .NET Core et .NET Standard ont des options sur la page des propriétés de l’analyse du code qui vous permettent de désactiver l’analyse du code des analyseurs installés en tant que package NuGet. Pour plus d’informations, consultez [.net Core et les projets .NET standard](#net-core-and-net-standard-projects). Pour désactiver l’analyse du code source pour les projets .NET Framework, consultez [.NET Framework projets](#net-framework-projects).

- Analyse de la source et analyse héritée

  Cette rubrique s’applique à l’analyse du code source et non à l’analyse héritée (binaire). Pour plus d’informations sur la désactivation de l’analyse héritée, consultez [Comment : activer et désactiver l’analyse du code hérité](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>Projets .NET Core et .NET Standard

À compter de Visual Studio 2019 version 16,3, deux cases à cocher sont disponibles dans la page des propriétés de l’analyse du code, qui vous permettent de contrôler si les analyseurs s’exécutent au moment de la génération et au moment de la conception. Ces options sont spécifiques au projet.

![Activer ou désactiver l’analyse du code en direct ou la génération dans Visual Studio](media/run-on-build-run-live-analysis.png)

Pour ouvrir cette page, cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** , puis sélectionnez **Propriétés**. Sélectionnez l’onglet **analyse du code** .

- Pour désactiver l’analyse de la source au moment de la génération, décochez l’option **exécuter sur la build** .
- Pour désactiver l’analyse de la source dynamique, décochez l’option **exécuter sur l’analyse en direct** .

> [!NOTE]
> À compter de Visual Studio 2019 version 16,5, si vous préférez le flux de travail d’exécution de l’analyse du code à la demande, vous pouvez désactiver l’exécution de l’analyseur lors de l’analyse en direct et/ou générer et déclencher manuellement l’analyse du code sur un projet ou une solution à la demande. Pour plus d’informations sur l’exécution manuelle de l’analyse du code, consultez [Comment : exécuter l’analyse du code manuellement pour le code managé](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="net-framework-projects"></a>Projets .NET Framework

Pour désactiver l’analyse du code source pour les analyseurs, ajoutez une ou plusieurs des propriétés MSBuild suivantes au [fichier projet](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| MSBuild, propriété | Description | Default |
| - | - | - |
| `RunAnalyzersDuringBuild` | Contrôle si les analyseurs s’exécutent au moment de la génération. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Contrôle si les analyseurs analysent le code en temps réel au moment de la conception. | `true` |
| `RunAnalyzers` | Désactive les analyseurs à la fois au moment de la génération et de la conception. Cette propriété est prioritaire sur `RunAnalyzersDuringBuild` et `RunAnalyzersDuringLiveAnalysis` . | `true` |

Exemples :

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Analyse du code source

Vous ne pouvez pas désactiver l’analyse de la [source](roslyn-analyzers-overview.md) dans Visual Studio 2017. Si vous souhaitez effacer les erreurs de l’analyseur de la **liste d’erreurs**, vous pouvez supprimer toutes les violations en cours en sélectionnant **analyser**  >  **exécuter l’analyse du code et supprimer les problèmes actifs** dans la barre de menus. Pour plus d’informations, consultez [Supprimer les violations](use-roslyn-analyzers.md#suppress-violations).

À compter de Visual Studio 2019 version 16,3, vous pouvez désactiver l’analyse du code source ou l’exécuter à la demande. Envisagez une mise à niveau vers Visual Studio 2019.

## <a name="legacy-analysis"></a>Analyse héritée

Vous pouvez désactiver l’analyse héritée au moment de la génération dans la page des propriétés de l' **analyse du code** . Pour plus d’informations, consultez [Comment : activer et désactiver l’analyse du code hérité](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Supprimer les violations](use-roslyn-analyzers.md#suppress-violations)
- [Comment : activer et désactiver l’analyse du code hérité](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
