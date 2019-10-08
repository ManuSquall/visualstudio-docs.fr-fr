---
title: Analyse du code à l’aide d’analyseurs Roslyn
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 844b9475ea59ba15ac96d3cbe19523f5cba63c72
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999987"
---
# <a name="overview-of-source-code-analyzers"></a>Vue d’ensemble des analyseurs de code source

Les analyseurs de code .NET Compiler Platform (« Roslyn ») C# inspectent votre code ou Visual Basic pour déterminer le style, la qualité, la facilité de gestion, la conception et d’autres problèmes.

- Certains analyseurs sont intégrés à Visual Studio. L’ID de diagnostic, ou code, de ces analyseurs est au format IDExxxx, par exemple, IDE0067. La plupart de ces analyseurs intégrés inspectent le [style du code](../ide/code-styles-and-code-cleanup.md)et vous pouvez configurer des préférences sur la [page Options](../ide/code-styles-and-code-cleanup.md) de l’éditeur de texte ou dans un [fichier EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Quelques analyseurs intégrés examinent la qualité du code.

- Vous pouvez installer des analyseurs supplémentaires sous la forme d’un package NuGet ou d’une extension Visual Studio. Exemple :

  - [Analyseurs FxCop](../code-quality/install-fxcop-analyzers.md), analyseurs de qualité de code recommandés par Microsoft
  - Analyseurs tiers, tels que [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator/), les [analyseurs xUnit](https://www.nuget.org/packages/xunit.analyzers/)et l' [analyseur sonar](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

Si des violations de règle sont détectées par un analyseur, elles sont signalées dans l’éditeur de code (sous forme de *tilde* sous le code incriminé) et dans la fenêtre de liste d’erreurs.

Un ou plusieurs *correctifs de code* que vous pouvez appliquer pour corriger le problème sont associés à de nombreuses règles d’analyseur, ou *diagnostics*. Les diagnostics d’analyseur qui sont intégrés à Visual Studio ont chacun un correctif de code qui leur est associé. Les correctifs de code sont affichés dans l’icône du menu Ampoule, avec d’autres types d’[Actions rapides](../ide/quick-actions.md). Pour plus d’informations sur ces correctifs de code, consultez [Actions rapides courantes](../ide/common-quick-actions.md).

![Violation d’analyseur et correctif de code par action rapide](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Analyse du code source et analyse héritée

L’analyse de la source par les analyseurs Roslyn remplace l' [analyse héritée](../code-quality/code-analysis-for-managed-code-overview.md) du code managé. La plupart des règles d’analyse héritées ont déjà été réécrites en tant qu’analyseurs de code Roslyn. Pour les modèles de projet plus récents tels que .NET Core et les projets .NET Standard, l’analyse héritée n’est même pas disponible.

À l’instar des violations des règles d’analyse héritées, les violations de l’analyse du code source s’affichent dans la fenêtre Liste d’erreurs dans Visual Studio. En outre, les violations de l’analyse du code source s’affichent également dans l’éditeur de code sous forme de *tildes* sous le code incriminé. La couleur de la ligne ondulée dépend du [paramètre de gravité](../code-quality/use-roslyn-analyzers.md#rule-severity) de la règle. L’illustration suivante montre trois violations @ no__t-0one rouge, un vert et un gris :

![Tildes dans l’éditeur de code dans Visual Studio](media/diagnostics-severity-colors.png)

Les analyseurs de code inspectent le code au moment de la génération, comme l’analyse héritée s’il est activé, mais également en cours de frappe. Si vous activez l’[analyse complète de la solution](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#toggle-full-solution-analysis), les analyseurs de code fournissent également une analyse au moment de la conception des fichiers de code qui ne sont pas ouverts dans l’éditeur.

> [!TIP]
> Les erreurs et les avertissements au moment de la génération provenant des analyseurs de code sont affichés uniquement si les analyseurs sont installés comme un package NuGet. Les analyseurs intégrés (par exemple, IDE0067 et IDE0068) ne s’exécutent jamais pendant la génération.

Non seulement les analyseurs de code Roslyn signalent les mêmes types de problèmes que l’analyse héritée, mais ils facilitent la résolution d’une ou de toutes les occurrences de la violation dans votre fichier ou projet. Ces actions sont appelées *correctifs de code*. Les correctifs de code sont spécifiques à l’IDE ; dans Visual Studio, elles sont implémentées en tant qu' [actions rapides](../ide/quick-actions.md). Tous les diagnostics d’analyseur ont un correctif de code associé.

> [!NOTE]
> L’option de menu **analyser** > **exécuter l’analyse du code** s’applique uniquement aux analyses héritées.

Pour faire la différence entre les violations des analyseurs de code et des analyses héritées dans la Liste d’erreurs, consultez la colonne **outil** . Si la valeur Outil correspond à l’un des assemblys d’analyseur dans l’**Explorateur de solutions**, par exemple **Microsoft.CodeQuality.Analyzers**, la violation provient d’un analyseur de code. Sinon, elle provient de l’analyse héritée.

![Colonne Outil dans la liste d’erreurs](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> La propriété MSBuild **RunCodeAnalysis** dans un fichier projet s’applique uniquement à l’analyse héritée. Si vous installez des analyseurs, affectez à **RunCodeAnalysis** la **valeur false** dans votre fichier projet pour empêcher l’exécution de l’analyse héritée après la génération.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Comparaison du package NuGet et de l’extension VSIX

Les analyseurs de code Roslyn peuvent être installés par projet par le biais d’un package NuGet. Certains sont également disponibles en tant qu’extension Visual Studio, auquel cas ils s’appliquent à toutes les solutions que vous ouvrez dans Visual Studio. Il existe certaines différences de comportement fondamentales entre ces deux méthodes [d’installation d’analyseurs](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>`Scope`

Si vous installez des analyseurs en tant qu’extension Visual Studio, ils s’appliquent au niveau de la solution et à toutes les instances de Visual Studio. Si vous installez les analyseurs comme un package NuGet, qui est la méthode recommandée, ils s’appliquent uniquement au projet dans lequel le package NuGet a été installé. Dans les environnements d’équipe, les analyseurs installés comme des packages NuGet se trouvent dans la portée de *tous les développeurs* qui travaillent sur ce projet.

### <a name="build-errors"></a>Erreurs de build

Pour que les règles soient appliquées au moment de la génération, notamment par le biais d’une génération en ligne de commande ou dans le cadre d’une build d’intégration continue (CI), installez les analyseurs comme un package NuGet. Les erreurs et avertissements d’analyseur ne s’affichent pas dans le rapport de build si vous installez les analyseurs comme une extension.

L’illustration suivante montre la sortie de la génération en ligne de commande de la génération d’un projet qui contient une violation de règle de l’analyseur :

![Sortie MSBuild avec violation de règle](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravité des règles

Vous ne pouvez pas configurer la gravité des règles à partir d’analyseurs qui ont été installés en tant qu’extension Visual Studio. Pour configurer la [gravité des règles](../code-quality/use-roslyn-analyzers.md#rule-severity), installez les analyseurs comme un package NuGet.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Installer des analyseurs de code dans Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Utiliser des analyseurs de code dans Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Voir aussi

- [FAQ sur les analyseurs](analyzers-faq.md)
- [Écrire votre propre analyseur de code](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
