---
title: Analyse de code FxCop et les analyseurs FxCop
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05dd0e01254bf1222a8a7de497b11ec2a808bfb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46136365"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Forum aux questions sur FxCop et FxCop analyseurs

Il peut être un peu difficile de comprendre les différences entre les systèmes hérités FxCop et FxCop analyseurs. Cet article vise à résoudre certains de vos questions que éventuelles.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Quelle est la différence entre les systèmes hérités FxCop et FxCop analyseurs ?

FxCop héritée exécute une analyse post-build sur un assembly compilé. Elle s’exécute comme un exécutable séparé appelé **FxCopCmd.exe**. FxCopCmd.exe charge l’assembly compilé, exécute l’analyse de code, puis signale les résultats (ou *diagnostics*).

Les analyseurs FxCop sont basées sur .NET Compiler Platform (« Roslyn »). Vous [installer sous la forme d’un package NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) qui est référencé par le projet ou la solution. Analyse basée sur les analyseurs FxCop exécuter du code source pendant l’exécution du compilateur. Les analyseurs FxCop sont hébergés au sein du processus du compilateur, soit **csc.exe** ou **vbc.exe**, et exécuter l’analyse quand le projet est généré. Résultats de l’analyseur sont signalées en même temps que les résultats du compilateur.

> [!NOTE]
> Vous pouvez également [installer des analyseurs FxCop en tant qu’une extension Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). Dans ce cas, les analyseurs de l’exécuter que vous tapez dans l’éditeur de code, mais ils ne s’exécute au moment de la génération. Si vous souhaitez exécuter des analyseurs FxCop dans le cadre de l’intégration continue (CI), les installer comme package NuGet à la place.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>La commande Exécuter l’analyse du Code s’exécute les analyseurs FxCop ?

Non. Lorsque vous sélectionnez **analyser** > **exécuter l’analyse du Code** dans Visual Studio 2017, il exécute l’analyse du code statique ou FxCop héritée. **Exécuter l’analyse du Code** n’a aucun effet sur les analyseurs de roslyn, y compris les analyseurs FxCop basée sur Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>La propriété de projet msbuild RunCodeAnalysis exécuter des analyseurs ?

Non. Le **RunCodeAnalysis** propriété dans un fichier projet (par exemple, *.csproj*) est utilisé uniquement pour exécuter FxCop héritée. Il s’exécute une tâche msbuild de post-build qui appelle **FxCopCmd.exe**. Cela revient à sélectionner **analyser** > **exécuter l’analyse du Code** dans Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Par conséquent, comment exécuter des analyseurs FxCop puis ?

Pour exécuter des analyseurs FxCop, tout d’abord [installer le package NuGet](install-fxcop-analyzers.md) pour eux. Puis générez votre projet ou solution à partir de Visual Studio ou à l’aide de msbuild. Les avertissements et erreurs qui génèrent les analyseurs FxCop apparaîtra dans le **liste d’erreurs** ou la fenêtre de commande.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Prise en main des analyseurs](fxcop-analyzers.yml)
- [Installer les analyseurs FxCop](install-fxcop-analyzers.md)
