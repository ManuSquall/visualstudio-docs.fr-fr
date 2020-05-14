---
title: Analyse du code à l’aide d’analyseurs Roslyn
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78a47cb2a5aefd7d20e0b8087f5f3ad735716175
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79431278"
---
# <a name="overview-of-source-code-analyzers"></a>Aperçu des analyseurs de code source

Les analyseurs de code .NET Compiler Platform («Roslyn») inspectent votre code de base graphique ou visuel pour obtenir du style, de la qualité et de la maintenance, de la conception et d’autres problèmes.

- Certains analyseurs sont intégrés à Visual Studio. L’ID diagnostique, ou code, pour ces analyseurs est du format IDExxxx, par exemple, IDE0067. La plupart de ces analyseurs intégrés inspectent le [style de code,](../ide/code-styles-and-code-cleanup.md)et vous pouvez configurer les préférences sur la [page d’options d’éditeur de texte](../ide/code-styles-and-code-cleanup.md) ou dans un fichier [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Une poignée d’analyseurs intégrés examinent la qualité du code.

- Vous pouvez installer des analyseurs supplémentaires sous forme d’un paquet NuGet ou d’une extension Visual Studio. Par exemple :

  - [Analyseurs FxCop](../code-quality/install-fxcop-analyzers.md), analyseurs de qualité de code recommandés par Microsoft
  - Analyseurs tiers, tels que [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), et [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

Si des violations de règles sont constatées par un analyseur, elles sont signalées dans l’éditeur de code (comme un *squiggle* sous le code incriminé) et dans la fenêtre de liste d’erreurs.

Un ou plusieurs *correctifs de code* que vous pouvez appliquer pour corriger le problème sont associés à de nombreuses règles d’analyseur, ou *diagnostics*. Les diagnostics d’analyseur qui sont intégrés à Visual Studio ont chacun un correctif de code qui leur est associé. Les correctifs de code sont affichés dans l’icône du menu Ampoule, avec d’autres types d’[Actions rapides](../ide/quick-actions.md). Pour plus d’informations sur ces correctifs de code, consultez [Actions rapides courantes](../ide/common-quick-actions.md).

![Violation d’analyseur et correctif de code par action rapide](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Analyse du code source par rapport à l’analyse de l’héritage

L’analyse source par les analyseurs Roslyn remplace [l’analyse héritée](../code-quality/code-analysis-for-managed-code-overview.md) du code géré. Bon nombre des règles d’analyse héritées ont déjà été réécrites en tant qu’analyseurs de code Roslyn. Pour les nouveaux modèles de projets tels que les projets .NET Core et .NET Standard, l’analyse de l’héritage n’est même pas disponible.

Comme les violations des règles d’analyse héritées, les violations de l’analyse du code source apparaissent dans la fenêtre Error List dans Visual Studio. En outre, les violations de l’analyse du code source apparaissent également dans l’éditeur de code comme *des gribouillis* en vertu du code incriminé. La couleur de la ligne ondulée dépend du [paramètre de gravité](../code-quality/use-roslyn-analyzers.md#rule-severity) de la règle. L’image suivante&mdash;montre trois violations, une rouge, une verte et une grise :

![Squiggles dans l’éditeur de code dans Visual Studio](media/diagnostics-severity-colors.png)

Les analyseurs de code inspectent le code au moment de la construction, comme l’analyse de l’héritage s’il est activé, mais aussi vivre comme vous tapez. Vous pouvez configurer la portée de l’analyse de code en direct pour exécuter uniquement le document actuel, tous les documents ouverts ou la solution complète. Voir [comment : Configurer la portée de l’analyse de code en direct](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Les erreurs et les avertissements au moment de la génération provenant des analyseurs de code sont affichés uniquement si les analyseurs sont installés comme un package NuGet. Les analyseurs intégrés (par exemple, IDE0067 et IDE0068) ne s’exécutent jamais pendant la construction.

Non seulement les analyseurs de code Roslyn signalent les mêmes types de problèmes que l’analyse héritée, mais ils vous permettent de corriger facilement un ou tous les cas de la violation dans votre fichier ou votre projet. Ces actions sont appelées *correctifs de code*. Les corrections de code sont spécifiques à l’IDE; dans Visual Studio, ils sont mis en œuvre comme [Actions rapides](../ide/quick-actions.md). Tous les diagnostics d’analyseur ont un correctif de code associé.

> [!NOTE]
> Avant la sortie du menu Visual Studio 2019 16.5, l’option de menu Analyse**de code d’exécution** **Analyze** > exécute l’analyse héritée. À partir de Visual Studio 2019 16.5, l’option de menu **d’analyse de code d’exécution** exécute des analyseurs basés sur Roslyn pour le projet ou la solution sélectionné.

Pour faire la distinction entre les violations des analyseurs de code et l’analyse de l’héritage dans la liste d’erreurs, regardez la colonne **d’outil.** Si la valeur Outil correspond à l’un des assemblys d’analyseur dans l’**Explorateur de solutions**, par exemple **Microsoft.CodeQuality.Analyzers**, la violation provient d’un analyseur de code. Sinon, elle provient de l’analyse héritée.

![Colonne Outil dans la liste d’erreurs](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> La propriété **RunCodeAnalysis** MSBuild dans un fichier de projet ne s’applique qu’à l’analyse de l’héritage. Si vous installez des analyseurs, définissez **RunCodeAnalysis** à **faux** dans votre fichier de projet, afin d’empêcher l’analyse héritée de s’exécuter après la construction.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Comparaison du package NuGet et de l’extension VSIX

Les analyseurs de code Roslyn peuvent être installés par projet via un paquet NuGet. Certains sont également disponibles sous forme d’extension Visual Studio, auquel cas ils s’appliquent à n’importe quelle solution que vous ouvrez dans Visual Studio. Il existe certaines différences de comportement fondamentales entre ces deux méthodes [d’installation d’analyseurs](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Étendue

Si vous installez des analyseurs comme extension Visual Studio, ils s’appliquent au niveau de la solution et à toutes les instances de Visual Studio. Si vous installez les analyseurs comme un package NuGet, qui est la méthode recommandée, ils s’appliquent uniquement au projet dans lequel le package NuGet a été installé. Dans les environnements d’équipe, les analyseurs installés comme des packages NuGet se trouvent dans la portée de *tous les développeurs* qui travaillent sur ce projet.

### <a name="build-errors"></a>Erreurs de build

Pour que les règles soient appliquées au moment de la génération, notamment par le biais d’une génération en ligne de commande ou dans le cadre d’une build d’intégration continue (CI), installez les analyseurs comme un package NuGet. Les erreurs et avertissements d’analyseur ne s’affichent pas dans le rapport de build si vous installez les analyseurs comme une extension.

L’image suivante montre la sortie de construction de la ligne de commande de la construction d’un projet qui contient une violation de règle d’analyseur :

![Sortie MSBuild avec violation de règle](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravité des règles

Vous ne pouvez pas configurer la sévérité des règles à partir d’analyseurs qui ont été installés comme une extension Visual Studio. Pour configurer la [gravité des règles](../code-quality/use-roslyn-analyzers.md#rule-severity), installez les analyseurs comme un package NuGet.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Installer des analyseurs de code dans Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Utiliser des analyseurs de code dans Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Voir aussi

- [FAQ sur les analyseurs](analyzers-faq.md)
- [Écrire votre propre analyseur de code](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
