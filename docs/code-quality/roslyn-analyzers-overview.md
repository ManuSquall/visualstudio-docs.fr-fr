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
ms.openlocfilehash: aaa989347744e015b90cca186c6aa9756dfe90fe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922295"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Vue d’ensemble des analyseurs de plateforme des compilateurs .NET

Visual Studio 2017 inclut un ensemble intégré d’analyseurs de plateforme des compilateurs .NET qui analysent votre code c# ou Visual Basic en cours de frappe. Vous pouvez installer des analyseurs supplémentaires comme une extension Visual Studio, ou sur une base par projet sous forme de package NuGet. Analyseurs examiner de style de code, la qualité du code et la facilité de maintenance, conception de code et d’autres problèmes.

Si les violations de règle sont détectées par un analyseur, ils sont signalés à la fois dans l’éditeur de code en tant qu’un *sinueux* sous le code douteux et dans le **liste d’erreurs**.

Analyseur de nombreuses règles ou *diagnostics*, ont un ou plusieurs *correctifs du code* que vous pouvez appliquer pour corriger le problème. Analyseur de diagnostics qui sont intégrées à Visual Studio ont un correctif de code associé. Correctifs de code sont affichés dans le menu d’icône d’ampoule, ainsi que d’autres types de *Actions rapides*. Pour plus d’informations sur ces correctifs de code, consultez [rapide des Actions courantes](../ide/common-quick-actions.md).

![Violation de l’analyseur et de correction du code Action rapide](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analyseurs de Roslyn et l’analyse statique du code

Les analyseurs de plateforme des compilateurs .NET (« Roslyn ») va remplacer [analyse statique du code](../code-quality/code-analysis-for-managed-code-overview.md) pour le code managé. Grand nombre de règles d’analyse du code statique ont déjà été réécrites en tant que tests de diagnostic Roslyn analyseur.

Comme les violations de règles d’analyse statique du code, les violations de Roslyn analyzer s’affichent dans le **liste d’erreurs**. En outre, les violations de Roslyn analyzer s’affichent également dans l’éditeur de code en tant que *tildes* sous le code douteux. La couleur de le des traits ondulés varie selon le [paramètre de gravité](../code-quality/use-roslyn-analyzers.md#rule-severity) de la règle. La capture d’écran suivante montre trois violations&mdash;un rouge, un vert et un gris :

![Tildes dans l’éditeur de code](media/diagnostics-severity-colors.png)

Analyseurs de Roslyn analyser le code au moment de la génération, comme l’analyse statique du code si elle est activée, mais également live en cours de frappe ! Analyseurs de Roslyn peuvent également fournir d’analyse au moment du design des fichiers de code qui ne sont pas ouverts dans l’éditeur si vous activez [l’analyse complète](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Erreurs de génération et les avertissements des analyseurs de Roslyn sont affichent uniquement si les analyseurs sont installés en tant que package NuGet.

Non seulement Roslyn analyseurs signalent les mêmes types de problèmes qui effectue de l’analyse statique du code, mais elles rendent facile pour vous permettre de résoudre une ou toutes, les occurrences de la violation ou de votre fichier projet. Ces actions sont appelées *correctifs du code*. Correctifs de code sont spécifiques à l’IDE ; dans Visual Studio, elles sont implémentées en tant que [Actions rapides](../ide/quick-actions.md). Pas de tous les diagnostics d’analyseur ont un correctif de code associé.

> [!NOTE]
> L’option de menu **analyser** > **exécuter l’analyse du Code** s’applique à l’analyse du code uniquement static. En outre, sur un projet **l’analyse du Code** page de propriétés, les **activer l’analyse du Code sur la Build** et **supprimer les résultats du code généré** cases à cocher s’applique uniquement à analyse statique du code. Ils n’ont aucun effet sur les analyseurs de Roslyn.

Pour différencier les violations des analyseurs de Roslyn et d’analyse statique du code dans le **liste d’erreurs**, examinez le **outil** colonne. Si la valeur de l’outil correspond à un des assemblys d’analyseur dans **l’Explorateur de solutions**, par exemple **Microsoft.CodeQuality.Analyzers**, un analyseur Roslyn provient de la violation. Dans le cas contraire, la violation provient de l’analyse statique du code.

![Colonne d’outil dans la liste d’erreurs](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-vs-extension"></a>Package NuGet et d’extension

Plateforme des compilateurs .NET analyseurs peuvent être installé par projet via un package NuGet, ou Visual Studio à l’échelle comme une extension Visual Studio. Il existe des différences de comportement de la touche entre ces deux méthodes de [l’installation des analyseurs de](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Portée

Si vous installez des analyseurs comme une extension Visual Studio, ils s’appliquent au niveau de la solution, à toutes les instances de Visual Studio. Si vous installez les analyseurs sous forme de package NuGet, qui est la méthode par défaut, ils s’appliquent uniquement au projet où le package NuGet a été installé. Dans les environnements d’équipe, les analyseurs installés comme packages NuGet sont dans la portée de *tous les développeurs* qui fonctionnent sur ce projet.

### <a name="build-errors"></a>Erreurs de build

Pour que les règles appliquées au moment de la génération, notamment via la ligne de commande ou dans le cadre d’une intégration continue (CI) génération, installez les analyseurs sous forme de package NuGet. Erreurs et avertissements de l’analyseur n’apparaissent pas dans le rapport de build si vous installez les analyseurs en tant qu’extension.

La capture d’écran suivante montre la sortie de génération de ligne de commande à partir de la génération d’un projet qui contient une violation de règle d’analyseur :

![Sortie de MSBuild avec violation de règle](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravité de la règle

Impossible de définir le niveau de gravité de règles à partir des analyseurs qui ont été installés dans une extension Visual Studio. Pour configurer [règle gravité](../code-quality/use-roslyn-analyzers.md#rule-severity), installez les analyseurs sous forme de package NuGet.

## <a name="next-steps"></a>Étapes suivantes

- [Installer des analyseurs de Roslyn dans Visual Studio](../code-quality/install-roslyn-analyzers.md)
- [Utiliser les analyseurs de Roslyn de Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Voir aussi

- [Actions rapides dans Visual Studio](../ide/quick-actions.md)
- [Écrire votre propre analyseur Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Plateforme de compilateurs .NET SDK](/dotnet/csharp/roslyn-sdk/)