---
title: Analyse du code à l’aide d’analyseurs Roslyn
ms.date: 03/26/2018
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 36985ab7a0ee94cb735b1954a9e5ea9c2e0d2bbf
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "57869094"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Vue d’ensemble des analyseurs .NET Compiler Platform

Les analyseurs .NET Compiler Platform (« Roslyn ») analysent votre code pour rechercher des problèmes de style, de qualité et de facilité de gestion, de conception et d’autres problèmes encore. Visual Studio comprend un ensemble intégré d’analyseurs qui analysent votre code C# et Visual Basic à mesure que vous l’écrivez. Vous configurez des préférences pour ces analyseurs intégrés sur la page [Options de l’éditeur de texte](../ide/code-styles-and-quick-actions.md) ou dans un [fichier .editorconfig](../ide/editorconfig-code-style-settings-reference.md). Vous pouvez installer des analyseurs supplémentaires sous la forme d’une extension Visual Studio ou d’un package NuGet.

Si des violations de règle sont trouvées par un analyseur, elles sont signalées à la fois dans l’éditeur de code (sous la forme d’une *ligne ondulée* sous le code problématique) et dans la fenêtre **Liste d’erreurs**.

Un ou plusieurs *correctifs de code* que vous pouvez appliquer pour corriger le problème sont associés à de nombreuses règles d’analyseur, ou *diagnostics*. Les diagnostics d’analyseur qui sont intégrés à Visual Studio ont chacun un correctif de code qui leur est associé. Les correctifs de code sont affichés dans l’icône du menu Ampoule, avec d’autres types d’[Actions rapides](../ide/quick-actions.md). Pour plus d’informations sur ces correctifs de code, consultez [Actions rapides courantes](../ide/common-quick-actions.md).

![Violation d’analyseur et correctif de code par action rapide](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Comparaison des analyseurs Roslyn et de l’analyse statique du code

Les analyseurs .NET Compiler Platform (« Roslyn ») remplaceront à terme [l’analyse statique du code](../code-quality/code-analysis-for-managed-code-overview.md) pour le code managé. Un grand nombre de règles d’analyse du code statique ont déjà été réécrites sous la forme de diagnostics d’analyseurs Roslyn.

Comme les violations des règles d’analyse statique du code, les violations d’analyseurs Roslyn s’affichent dans la **Liste d’erreurs**. De plus, les violations d’analyseurs Roslyn s’affichent également dans l’éditeur de code sous la forme de *lignes ondulées* sous le code problématique. La couleur de la ligne ondulée dépend du [paramètre de gravité](../code-quality/use-roslyn-analyzers.md#rule-severity) de la règle. La capture d’écran suivante montre trois violations (une rouge, une verte et une grise) :

![Lignes ondulées dans l’éditeur de code](media/diagnostics-severity-colors.png)

Les analyseurs Roslyn analysent le code au moment de la génération, comme l’analyse statique du code si elle est activée, mais également à mesure que vous tapez. Si vous activez l’[analyse complète de la solution](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis), les analyseurs Roslyn fournissent également une analyse au moment de la conception des fichiers de code qui ne sont pas ouverts dans l’éditeur.

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

- [FAQ sur les analyseurs](analyzers-faq.md)
- [Écrire votre propre analyseur Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)