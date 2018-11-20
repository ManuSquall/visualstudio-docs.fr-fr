---
title: Analyseurs Roslyn dans Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3d5836c0522ef97a634f44799934aab2750b3a45
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511420"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Vue d’ensemble des analyseurs .NET Compiler Platform

Visual Studio 2017 comprend un ensemble intégré d’analyseurs .NET Compiler Platform qui analysent votre code C# et Visual Basic à mesure que vous tapez. Vous pouvez installer des analyseurs supplémentaires comme une extension Visual Studio ou par projet comme un package NuGet. Les analyseurs observent le style du code, la qualité et facilité de gestion du code, la conception du code, ainsi que d’autres problèmes.

Si des violations de règle sont trouvées par un analyseur, elles sont signalées à la fois dans l’éditeur de code sous la forme d’une *ligne ondulée* sous le code problématique et dans la **liste d’erreurs**.

Un ou plusieurs *correctifs de code* que vous pouvez appliquer pour corriger le problème sont associés à de nombreuses règles d’analyseur, ou *diagnostics*. Les diagnostics d’analyseur qui sont intégrés à Visual Studio ont chacun un correctif de code qui leur est associé. Les correctifs de code sont affichés dans l’icône du menu Ampoule, avec d’autres types *d’actions rapides*. Pour plus d’informations sur ces correctifs de code, consultez [Actions rapides courantes](../ide/common-quick-actions.md).

![Violation d’analyseur et correctif de code par action rapide](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Comparaison des analyseurs Roslyn et de l’analyse statique du code

Les analyseurs .NET Compiler Platform (« Roslyn ») remplaceront à terme [l’analyse statique du code](../code-quality/code-analysis-for-managed-code-overview.md) pour le code managé. Un grand nombre de règles d’analyse du code statique ont déjà été réécrites sous la forme de diagnostics d’analyseurs Roslyn.

Comme les violations des règles d’analyse statique du code, les violations d’analyseurs Roslyn s’affichent dans la **liste d’erreurs**. De plus, les violations d’analyseurs Roslyn s’affichent également dans l’éditeur de code sous la forme de *lignes ondulées* sous le code problématique. La couleur de la ligne ondulée dépend du [paramètre de gravité](../code-quality/use-roslyn-analyzers.md#rule-severity) de la règle. La capture d’écran suivante montre trois violations (une rouge, une verte et une grise) :

![Lignes ondulées dans l’éditeur de code](media/diagnostics-severity-colors.png)

Les analyseurs Roslyn analysent le code au moment de la génération, comme l’analyse statique du code si elle est activée, mais également à mesure que vous tapez. Les analyseurs Roslyn peuvent également fournir une analyse au moment du design des fichiers de code qui ne sont pas ouverts dans l’éditeur si vous activez [l’analyse complète de la solution](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Les erreurs et les avertissements au moment de la génération provenant des analyseurs Roslyn sont affichés uniquement si les analyseurs sont installés comme un package NuGet.

Non seulement les analyseurs Roslyn signalent les mêmes types de problèmes que l’analyse statique du code, mais ils vous permettent de résoudre facilement une occurrence de la violation, ou toutes, dans votre fichier ou projet. Ces actions sont appelées *correctifs de code*. Les correctifs de code sont spécifiques à l’IDE. Dans Visual Studio, ils sont implémentés sous la forme [d’actions rapides](../ide/quick-actions.md). Tous les diagnostics d’analyseur ont un correctif de code associé.

> [!NOTE]
> L’option de menu **Analyser** > **Exécuter l’analyse du code** s’applique uniquement à l’analyse statique du code . De plus, sur la page de propriétés **Analyse du code** d’un projet, les cases à cocher **Activer l’analyse du code sur la build** et **Supprimer les résultats du code généré** s’appliquent uniquement à l’analyse statique du code. Elles n’ont aucun effet sur les analyseurs Roslyn.

Pour différencier les violations d’analyseurs Roslyn et de celles de l’analyse statique du code dans la **liste d’erreurs**, examinez la colonne **Outil**. Si la valeur Outil correspond à l’un des assemblys d’analyseur dans **l’Explorateur de solutions**, par exemple **Microsoft.CodeQuality.Analyzers**, la violation provient d’un analyseur Roslyn. Sinon, la violation provient de l’analyse statique du code.

![Colonne Outil dans la liste d’erreurs](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-versus-vsix-extension"></a>Comparaison du package NuGet et de l’extension VSIX

Les analyseurs .NET Compiler Platform peuvent être installés par projet par le biais d’un package NuGet, ou à l’échelle de Visual Studio comme une extension Visual Studio. Il existe certaines différences de comportement fondamentales entre ces deux méthodes [d’installation d’analyseurs](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Portée

Si vous installez des analyseurs comme une extension Visual Studio, ils s’appliquent au niveau de la solution, à toutes les instances de Visual Studio. Si vous installez les analyseurs comme un package NuGet, qui est la méthode recommandée, ils s’appliquent uniquement au projet dans lequel le package NuGet a été installé. Dans les environnements d’équipe, les analyseurs installés comme des packages NuGet se trouvent dans la portée de *tous les développeurs* qui travaillent sur ce projet.

### <a name="build-errors"></a>Erreurs de build

Pour que les règles soient appliquées au moment de la génération, notamment par le biais d’une génération en ligne de commande ou dans le cadre d’une build d’intégration continue (CI), installez les analyseurs comme un package NuGet. Les erreurs et avertissements d’analyseur ne s’affichent pas dans le rapport de build si vous installez les analyseurs comme une extension.

La capture d’écran suivante montre la sortie de la génération en ligne de commande à partir de la génération d’un projet qui contient une violation de règle d’analyseur :

![Sortie MSBuild avec violation de règle](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravité des règles

Vous ne pouvez pas définir la gravité des règles à partir des analyseurs qui ont été installés comme une extension Visual Studio. Pour configurer la [gravité des règles](../code-quality/use-roslyn-analyzers.md#rule-severity), installez les analyseurs comme un package NuGet.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Installez des analyseurs Roslyn dans Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Utiliser des analyseurs Roslyn dans Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Voir aussi

- [Actions rapides en Visual Studio](../ide/quick-actions.md)
- [Écrire votre propre analyseur Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)