---
title: Analyse de code FxCop et analyseurs FxCop
ms.date: 09/06/2018
description: Comprenez la différence entre les analyseurs FxCop et FxCop hérités dans Visual Studio. Consultez les réponses aux questions sur l’utilisation de ces analyseurs.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e6768ad7f1ee87f75592c736b03bf6fd64e28c2
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348956"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Questions fréquentes (FAQ) sur FxCop et les analyseurs FxCop

Il peut être un peu difficile de comprendre les différences entre les analyseurs FxCop et FxCop hérité. Cet article vise à répondre à certaines des questions que vous pouvez vous poser.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Quelle est la différence entre les analyseurs FxCop et FxCop hérité ?

FxCop hérité exécute une analyse post-build sur un assembly compilé. Il s’exécute en tant qu’exécutable distinct appelé **FxCopCmd.exe**. FxCopCmd.exe charge l’assembly compilé, exécute l’analyse du code, puis signale les résultats (ou *diagnostics* ).

Les analyseurs FxCop sont basés sur .NET Compiler Platform (« Roslyn »). Vous [les installez comme package NuGet](install-fxcop-analyzers.md#nuget-package) référencé par le projet ou la solution. Les analyseurs FxCop exécutent une analyse basée sur le code source pendant l’exécution du compilateur. Les analyseurs FxCop sont hébergés dans le processus du compilateur, **csc.exe** ou **vbc.exe** , et exécutent l’analyse quand le projet est généré. Les résultats des analyseurs sont signalés en même temps que les résultats du compilateur.

> [!NOTE]
> Vous pouvez également [installer des analyseurs FxCop en tant qu’extension Visual Studio](install-fxcop-analyzers.md#vsix). Dans ce cas, les analyseurs s’exécutent quand vous tapez dans l’éditeur de code, mais pas au moment de la génération. Si vous voulez exécuter des analyseurs FxCop dans le cadre de l’intégration continue (CI), installez-les en tant que package NuGet à la place.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>La commande Exécuter l’analyse du Code exécute-t-elle les analyseurs FxCop ?

Avant Visual Studio 2019, version 16,5, lorsque vous sélectionnez **analyser**  >  **exécuter l’analyse du code** , l’analyse héritée est exécutée. À compter de Visual Studio 2019 16,5, l’option de menu **exécuter l’analyse du code** exécute des analyseurs Roslyn pour la solution ou le projet sélectionné. Si vous avez installé les analyseurs FxCop Roslyn, ils sont également exécutés. Pour plus d’informations, consultez [Comment : exécuter l’analyse du code manuellement pour le code managé](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>La propriété de projet msbuild RunCodeAnalysis exécute-t-elle des analyseurs ?

Non. La propriété **RunCodeAnalysis** dans un fichier projet (par exemple, *.csproj* ) est utilisée uniquement pour exécuter FxCop hérité. Elle s’exécute une tâche msbuild post-build qui appelle **FxCopCmd.exe**.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Alors, comment exécuter des analyseurs FxCop ?

Pour exécuter des analyseurs FxCop, commencez par [installer le package NuGet](install-fxcop-analyzers.md) correspondant à ces derniers. Générez ensuite votre projet ou solution à partir de Visual Studio ou à l’aide de msbuild. Les avertissements et erreurs que génèrent les analyseurs FxCop s’affichent dans la **liste d’erreurs** ou la fenêtre Commande.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Je reçois l’avertissement CA0507 même après avoir installé le package NuGet d’analyseurs FxCop

Si vous avez installé les analyseurs FxCop, mais que vous continuez à obtenir l’avertissement CA0507 **« l’exécution de l’analyse du code » est dépréciée en faveur des analyseurs FxCop, qui s’exécutent pendant la génération»** , vous devrez peut-être affecter la valeur **false** à la propriété MSBuild **RunCodeAnalysis** dans votre [fichier projet](../ide/solutions-and-projects-in-visual-studio.md#project-file) . Dans le cas contraire, l’analyse héritée s’exécutera après chaque génération.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>Quelles règles ont été portées vers les analyseurs FxCop ?

Pour plus d’informations sur les règles d’analyse héritées qui ont été portées vers les [analyseurs FxCop](install-fxcop-analyzers.md), consultez État du port de la [règle FXCop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Les avertissements d’analyse du code sont traités comme des erreurs

Si votre projet utilise l’option de build pour traiter les avertissements comme des erreurs, les avertissements de l’analyseur FxCop peuvent apparaître comme des erreurs. Pour empêcher que des avertissements d’analyse du code ne soient traités comme des erreurs, suivez les étapes indiquées dans FAQ sur l' [analyse du code](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migrer vers des analyseurs FxCop](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [Installer des analyseurs FxCop](install-fxcop-analyzers.md)
