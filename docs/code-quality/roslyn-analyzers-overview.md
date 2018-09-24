---
title: Analyseurs de Roslyn dans Visual Studio
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
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511420"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Vue d’ensemble des analyseurs de .NET Compiler Platform

Visual Studio 2017 inclut un ensemble intégré d’analyseurs .NET Compiler Platform qui analysent votre code c# ou Visual Basic en cours de frappe. Vous pouvez installer des analyseurs supplémentaires comme une extension Visual Studio, ou sur une base par projet sous forme de package NuGet. Analyseurs recherchent au style de code, la qualité du code et la facilité de maintenance, conception de code et d’autres problèmes.

Si des violations de règle sont trouvées par un analyseur, elles sont signalées à la fois dans l’éditeur de code comme un *ondulée* sous le code incriminé, puis, dans le **liste d’erreurs**.

Analyseur de nombreuses règles ou *diagnostics*, un ou plusieurs associés *corrections de code* que vous pouvez appliquer pour corriger le problème. Analyseur de diagnostics qui sont intégrées à Visual Studio ont un correctif de code associé. Correctifs de code sont affichés dans le menu de l’icône ampoule, ainsi que d’autres types de *Actions rapides*. Pour plus d’informations sur ces correctifs de code, consultez [Actions rapides courantes](../ide/common-quick-actions.md).

![Violation de l’analyseur et correctif de code d’Action rapide](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analyseurs de Roslyn et l’analyse statique du code

Les analyseurs .NET compiler Platform (« Roslyn ») va remplacer [analyse statique du code](../code-quality/code-analysis-for-managed-code-overview.md) pour le code managé. Grand nombre de règles d’analyse du code statique ont déjà été réécrites comme diagnostics d’analyseur Roslyn.

Comme les violations de règle d’analyse statique du code, les violations d’analyseur Roslyn s’affichent dans le **liste d’erreurs**. En outre, les violations d’analyseur Roslyn apparaissent également dans l’éditeur de code en tant que *tildes* sous le code douteux. La couleur de la ligne ondulée varie selon le [paramètre de gravité](../code-quality/use-roslyn-analyzers.md#rule-severity) de la règle. La capture d’écran suivante montre trois violations&mdash;un rouge, un vert et un gris :

![Tildes dans l’éditeur de code](media/diagnostics-severity-colors.png)

Analyseurs de Roslyn analyser le code au moment de la génération, comme l’analyse statique du code si elle est activée, mais également live en cours de frappe ! Analyseurs de Roslyn peuvent également fournir d’analyse au moment du design des fichiers de code qui ne sont pas ouverts dans l’éditeur si vous activez [complète d’analyse de la solution](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Erreurs de génération et avertissements des analyseurs de Roslyn sont affichent uniquement si les analyseurs sont installés sous forme de package NuGet.

Non seulement les analyseurs de Roslyn signalent les mêmes types de problèmes qui effectue l’analyse du code statique, mais ils facilitent pour vous permettre de résoudre une ou toutes, les occurrences de la violation ou de votre fichier projet. Ces actions sont appelées *corrections de code*. Correctifs de code sont spécifiques à l’IDE ; dans Visual Studio, ils sont implémentés en tant que [Actions rapides](../ide/quick-actions.md). Pas tous les diagnostics d’analyzer ont un correctif de code associé.

> [!NOTE]
> L’option de menu **analyser** > **exécuter l’analyse du Code** s’applique à l’analyse du code uniquement comme étant statique. En outre, sur un projet **analyse du Code** page de propriétés, la **activer l’analyse du Code sur la Build** et **supprimer les résultats du code généré** cases à cocher s’appliquent uniquement aux analyse statique du code. Ils n’ont aucun effet sur les analyseurs de Roslyn.

Faire la distinction entre les violations d’analyseurs de Roslyn et l’analyse statique du code dans le **liste d’erreurs**, examinez le **outil** colonne. Si la valeur de l’outil correspond à l’un des assemblys d’analyseur dans **l’Explorateur de solutions**, par exemple **Microsoft.CodeQuality.Analyzers**, la violation provient d’un analyseur Roslyn. Sinon, la violation proviennent de l’analyse statique du code.

![Colonne d’outil dans la liste d’erreurs](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-versus-vsix-extension"></a>Package NuGet ou d’extension VSIX

.NET compiler Platform analyseurs peuvent être installé par le projet via un package NuGet, ou Visual Studio à l’échelle comme une extension Visual Studio. Il existe des différences de comportement de la touche entre ces deux méthodes de [l’installation d’analyseurs](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Portée

Si vous installez des analyseurs comme une extension Visual Studio, ils s’appliquent au niveau de la solution, à toutes les instances de Visual Studio. Si vous installez les analyseurs sous forme de package NuGet, qui est la méthode préférée, ils s’appliquent uniquement au projet dans lequel le package NuGet a été installé. Dans les environnements d’équipe, les analyseurs installés en tant que packages NuGet sont dans la portée de *tous les développeurs* qui fonctionnent sur ce projet.

### <a name="build-errors"></a>Erreurs de build

Pour que les règles appliquées au moment de la génération, y compris via la ligne de commande ou dans le cadre d’une intégration continue (CI) build, installez les analyseurs sous forme de package NuGet. Erreurs et avertissements de l’analyseur n’apparaissent pas dans le rapport de génération si vous installez les analyseurs en tant qu’extension.

La capture d’écran suivante montre la sortie de génération de ligne de commande à partir de la génération d’un projet qui contient une violation de règle analyzer :

![Sortie MSBuild avec violation de règle](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravité de la règle

Impossible de définir le niveau de gravité de règles à partir des analyseurs qui ont été installés en tant qu’une extension Visual Studio. Pour configurer [gravité de règle](../code-quality/use-roslyn-analyzers.md#rule-severity), installer les analyseurs sous forme de package NuGet.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Installer des analyseurs de Roslyn dans Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Utiliser les analyseurs de Roslyn dans Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Voir aussi

- [Actions rapides dans Visual Studio](../ide/quick-actions.md)
- [Écrire votre propre analyseur Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Kit SDK .NET compiler Platform](/dotnet/csharp/roslyn-sdk/)