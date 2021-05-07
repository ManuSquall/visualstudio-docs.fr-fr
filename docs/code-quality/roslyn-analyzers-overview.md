---
title: Analyse du code à l’aide d’analyseurs Roslyn
ms.date: 09/01/2020
description: Familiarisez-vous avec l’analyse du code source dans Visual Studio. En savoir plus sur les correctifs de code et les différents types d’analyseurs et de niveaux de gravité.
ms.custom: SEO-VS-2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c3a7192ac55dc4138746e3e1e1abe4eaa6928395
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798334"
---
# <a name="overview-of-source-code-analysis"></a>Vue d’ensemble de l’analyse du code source

Les analyseurs de .NET Compiler Platform (Roslyn) inspectent votre code C# ou Visual Basic pour déterminer le style, la qualité, la maintenabilité, la conception et d’autres problèmes. Cette inspection ou analyse est effectuée au moment de la conception dans tous les fichiers ouverts.

Les analyseurs peuvent être répartis dans les groupes suivants :

- Les analyseurs de [style de code](/dotnet/fundamentals/code-analysis/code-style-rule-options?preserve-view=true&view=vs-2019#convention-categories) sont intégrés à Visual Studio. L’ID de diagnostic, ou code, de ces analyseurs est au format IDExxxx, par exemple, IDE0067. Vous pouvez configurer des préférences dans la [page Options](../ide/code-styles-and-code-cleanup.md) de l’éditeur de texte ou dans un [fichier EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options). À compter de .NET 5,0, les analyseurs de style de code sont inclus dans le kit de développement logiciel (SDK) .NET et peuvent être strictement appliqués sous forme d’avertissements ou d’erreurs de génération. Vous pourrez trouver plus d’informations [ici](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis).

- Les analyseurs de la [qualité du code](/dotnet/fundamentals/code-analysis/quality-rules/index) sont désormais fournis avec le kit de développement logiciel (SDK) .net 5 et sont activés par défaut. L’ID de diagnostic, ou code, de ces analyseurs est au format CAXXXX, par exemple, CA1822. Pour plus d’informations, consultez [vue d’ensemble de l’analyse de la qualité du code .net](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis).

- Les analyseurs tiers peuvent être installés en tant que package NuGet ou extension Visual Studio. Analyseurs tiers, tels que [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), les [analyseurs xUnit](https://www.nuget.org/packages/xunit.analyzers/)et l' [analyseur sonar](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).

## <a name="severity-levels-of-analyzers"></a>Niveaux de gravité des analyseurs

Chaque analyseur a l’un des niveaux de gravité suivants :

| Gravité (Explorateur de solutions) | Gravité (fichier EditorConfig) | Comportement au moment de la génération | Comportement de l’éditeur |
|-|-|-|
| Error | `error` | Les violations apparaissent comme des *Erreurs* dans les liste d’erreurs et dans la sortie de la génération en ligne de commande, et entraînent l’échec des builds.| Le code incriminé est souligné d’un tilde rouge et marqué d’une petite zone rouge dans la barre de défilement. |
| Avertissement | `warning` | Les violations apparaissent en tant qu' *avertissements* dans le liste d’erreurs et dans la sortie de la génération en ligne de commande, mais ne provoquent pas l’échec des builds. | Le code incriminé est souligné d’un tilde vert et est marqué d’un petit cadre vert dans la barre de défilement. |
| Informations | `suggestion` | Les violations apparaissent sous la forme de *messages* dans le liste d’erreurs, et pas du tout dans la sortie de la génération de la ligne de commande. | Le code incriminé est souligné d’un tilde gris et marqué d’une petite zone grise dans la barre de défilement. |
| Hidden | `silent` | Non visible par l’utilisateur. | Non visible par l’utilisateur. Toutefois, le diagnostic est signalé au moteur de diagnostic IDE. |
| Aucun | `none` | Entièrement supprimée. | Entièrement supprimée. |
| Par défaut | `default` | Correspond à la gravité par défaut de la règle. Pour déterminer la valeur par défaut d’une règle, recherchez dans la Fenêtre Propriétés. | Correspond à la gravité par défaut de la règle. |

Si des violations de règle sont détectées par un analyseur, elles sont signalées dans l’éditeur de code (sous forme de *tilde* sous le code incriminé) et dans la fenêtre de liste d’erreurs.

![Violation de l’analyseur dans la fenêtre Liste d’erreurs](../code-quality/media/code-analysis-error-list.png)

Les violations de l’analyseur signalées dans la liste d’erreurs correspondent au [paramètre de niveau de gravité](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) de la règle. Les violations de l’analyseur s’affichent également dans l’éditeur de code sous forme de tildes sous le code incriminé. L’illustration suivante montre trois violations d' &mdash; une erreur (tilde rouge), un avertissement (tilde vert) et une suggestion (trois points gris) :

![Tildes dans l’éditeur de code dans Visual Studio](media/diagnostics-severity-colors.png)

De nombreuses règles de l’analyseur, ou *Diagnostics*, ont une ou plusieurs *corrections de code* associées que vous pouvez appliquer pour corriger la violation de règle. Les correctifs de code sont affichés dans l’icône du menu Ampoule, avec d’autres types d’[Actions rapides](../ide/quick-actions.md). Pour plus d’informations sur ces correctifs de code, consultez [Actions rapides courantes](../ide/quick-actions.md).

![Violation d’analyseur et correctif de code par action rapide](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Configurer les niveaux de gravité de l’analyseur

Vous pouvez configurer la gravité des règles de l’analyseur ou des *Diagnostics* dans un [fichier EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) ou à partir du [menu ampoule](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu).

Les analyseurs peuvent également être configurés pour inspecter le code au moment de la génération et en temps réel à mesure que vous tapez. Vous pouvez configurer l’étendue de l’analyse dynamique du code pour qu’elle s’exécute uniquement pour le document actif, pour tous les documents ouverts ou pour l’ensemble de la solution. Consultez [Comment : configurer l’étendue de l’analyse du code en direct](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Les erreurs et les avertissements au moment de la génération provenant des analyseurs de code sont affichés uniquement si les analyseurs sont installés comme un package NuGet. Les analyseurs intégrés (par exemple, IDE0067 et IDE0068) ne s’exécutent jamais pendant la génération.

## <a name="nuget-package-versus-vsix-extension"></a>Comparaison du package NuGet et de l’extension VSIX

Les analyseurs tiers peuvent être installés par projet par le biais d’un package NuGet. Certains sont également disponibles en tant qu’extension Visual Studio, auquel cas ils s’appliquent à toutes les solutions que vous ouvrez dans Visual Studio. Il existe certaines différences de comportement fondamentales entre ces deux méthodes [d’installation d’analyseurs](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Étendue

Si vous installez des analyseurs en tant qu’extension Visual Studio, ils s’appliquent au niveau de la solution et à toutes les instances de Visual Studio. Si vous installez les analyseurs comme un package NuGet, qui est la méthode recommandée, ils s’appliquent uniquement au projet dans lequel le package NuGet a été installé. Dans les environnements d’équipe, les analyseurs installés comme des packages NuGet se trouvent dans la portée de *tous les développeurs* qui travaillent sur ce projet.

### <a name="build-errors"></a>Erreurs de build

Pour que les règles soient appliquées au moment de la génération, y compris via la ligne de commande ou dans le cadre d’une build d’intégration continue, vous pouvez choisir l’une des options suivantes :

- Créez un projet .NET 5,0 qui comprend des analyseurs par défaut dans le kit de développement logiciel (SDK) .NET. L’analyse du code est activée par défaut pour les projets ciblant .NET 5.0 ou ultérieur. Vous pouvez activer l’analyse du code sur des projets qui ciblent des versions antérieures de .NET en affectant à la propriété [EnableNETAnalyzers](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) la valeur true.

- Installer des analyseurs en tant que package NuGet. Les erreurs et avertissements d’analyseur ne s’affichent pas dans le rapport de build si vous installez les analyseurs comme une extension.

L’illustration suivante montre la sortie de la génération en ligne de commande de la génération d’un projet qui contient une violation de règle de l’analyseur :

![Sortie MSBuild avec violation de règle](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravité des règles

Vous ne pouvez pas configurer la gravité des règles à partir d’analyseurs qui ont été installés en tant qu’extension Visual Studio. Pour configurer la [gravité des règles](../code-quality/use-roslyn-analyzers.md#configure-severity-levels), installez les analyseurs comme un package NuGet.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Installer des analyseurs de code dans Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Utiliser des analyseurs de code dans Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Voir aussi

- [FAQ sur les analyseurs](analyzers-faq.yml)
- [Écrire votre propre analyseur de code](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)