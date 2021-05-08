---
title: Analyse du code FxCop (analyse binaire) et analyseurs .NET (analyse de la source)
ms.date: 09/06/2018
description: Comprenez la différence entre les analyseurs FxCop hérités (analyse binaire) et .NET (analyse de code source) dans Visual Studio. Consultez les réponses aux questions sur l’utilisation de ces analyseurs.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 951e9b951f1d90077fe29506e9c288fb19f2d5ff
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800503"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Forum aux questions sur les analyseurs FxCop et .NET hérités

Il peut être difficile de comprendre les différences entre les analyseurs FxCop hérités (binaires) et les analyseurs .NET (analyse de code source). Cet article vise à répondre à certaines des questions que vous pouvez vous poser.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>Quelle est la différence entre les analyseurs FxCop et .NET hérités ?

FxCop hérité exécute une analyse post-build sur un assembly compilé. Il s’exécute en tant qu’exécutable distinct appelé **FxCopCmd.exe**. FxCopCmd.exe charge l’assembly compilé, exécute l’analyse du code, puis signale les résultats (ou *diagnostics*).

Les analyseurs .NET sont basés sur le .NET Compiler Platform (« Roslyn »). Vous les [activez à partir du kit de développement logiciel (SDK) .net ou vous les installez en tant que package NuGet](install-net-analyzers.md) référencé par le projet ou la solution. Les analyseurs exécutent une analyse basée sur le code source lors de l’exécution du compilateur. Les analyseurs sont hébergés dans le processus du compilateur, **csc.exe** ou **vbc.exe**, et exécuter une analyse lorsque le projet est généré. Les résultats des analyseurs sont signalés en même temps que les résultats du compilateur.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>Quelle est la différence entre les analyseurs FxCop et les analyseurs .NET ?

Les analyseurs FxCop et les analyseurs .NET font référence aux implémentations de l’analyseur de .NET Compiler Platform (« Roslyn ») des règles d’autorité de certification FxCop. Avant Visual Studio 2019 16,8 et .NET 5,0, ces analyseurs étaient fournis sous forme de `Microsoft.CodeAnalysis.FxCopAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). À compter de Visual Studio 2019 16,8 et .NET 5,0, ces analyseurs sont [inclus dans le kit de développement logiciel (SDK) .net](/dotnet/fundamentals/code-analysis/overview). Ils sont également disponibles en tant que `Microsoft.CodeAnalysis.NetAnalyzers` [package NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Envisagez [de migrer des analyseurs FxCop vers des analyseurs .net](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>La commande exécuter l’analyse du code exécute-t-elle des analyseurs .NET ?

Avant Visual Studio 2019, version 16,5, lorsque vous sélectionnez **analyser**  >  **exécuter l’analyse du code**, l’analyse héritée est exécutée. À compter de Visual Studio 2019 16,5, l’option de menu **exécuter l’analyse du code** exécute des analyseurs Roslyn pour la solution ou le projet sélectionné. Si vous avez installé les analyseurs .NET, ils sont également exécutés. Pour plus d’informations, consultez [Comment : exécuter l’analyse du code manuellement pour le code managé](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>La propriété de projet msbuild RunCodeAnalysis exécute-t-elle des analyseurs ?

Non. La propriété **RunCodeAnalysis** dans un fichier projet (par exemple, *.csproj*) est utilisée uniquement pour exécuter FxCop hérité. Elle s’exécute une tâche msbuild post-build qui appelle **FxCopCmd.exe**.

## <a name="so-how-do-i-run-net-analyzers-then"></a>Comment puis-je exécuter des analyseurs .NET ?

Pour exécuter des analyseurs .NET, commencez par les [activer à partir du kit de développement logiciel (SDK) .net ou installez-les en tant que package NuGet](install-net-analyzers.md). Générez ensuite votre projet ou solution à partir de Visual Studio ou à l’aide de msbuild. Les avertissements et erreurs générés par les analyseurs Roslyn s’affichent dans la **liste d’erreurs** ou dans la fenêtre de commande.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>J’obtiens un avertissement CA0507 même après l’installation du package NuGet des analyseurs .NET

Si vous avez installé les analyseurs .NET, mais que vous continuez à obtenir l’avertissement CA0507 **« l’exécution de l’analyse du code » est dépréciée en faveur des analyseurs FxCop, qui s’exécutent pendant la génération»**, vous devrez peut-être affecter la valeur **false** à la propriété MSBuild **RunCodeAnalysis** dans votre [fichier projet](../ide/solutions-and-projects-in-visual-studio.md#project-file) . Dans le cas contraire, l’analyse héritée s’exécutera après chaque génération.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>Quelles règles ont été portées vers les analyseurs .NET ?

Pour plus d’informations sur les règles d’analyse héritées qui ont été portées vers les analyseurs .NET, consultez l’état du port de la [règle FXCop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Les avertissements d’analyse du code sont traités comme des erreurs

Si votre projet utilise l’option de build pour traiter les avertissements comme des erreurs, les avertissements de l’analyseur peuvent apparaître comme des erreurs. Pour empêcher que des avertissements d’analyse du code ne soient traités comme des erreurs, suivez les étapes indiquées dans FAQ sur l' [analyse du code](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migrer vers les analyseurs .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Installer les analyseurs .NET](install-net-analyzers.md)
