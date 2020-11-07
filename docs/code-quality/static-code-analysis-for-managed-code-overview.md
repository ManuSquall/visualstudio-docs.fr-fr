---
title: Analyse héritée pour le code managé
ms.date: 06/12/2019
description: En savoir plus sur les analyses héritées dans Visual Studio. Découvrez comment supprimer des avertissements et comment exécuter des analyses manuellement, automatiquement et Pendant les archivages et les builds.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c6f1f12fa7fca964c857e534c1ffae50efe70b27
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348656"
---
# <a name="overview-of-legacy-analysis-for-managed-code-in-visual-studio"></a>Vue d’ensemble de l’analyse héritée du code managé dans Visual Studio

Visual Studio peut effectuer une analyse du code managé de deux manières : avec l' [analyse héritée](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), également appelée analyse statique FxCop des assemblys managés, et avec les [analyseurs de code](../code-quality/roslyn-analyzers-overview.md)plus modernes basés sur le .NET Compiler Platform. Cette rubrique traite des analyses héritées. Pour en savoir plus sur l’analyse du code basé sur .NET Compiler Platform, consultez [vue d’ensemble des analyseurs basés sur des .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md).

L’analyse du code managé analyse les assemblys managés et fournit des informations sur les assemblys, telles que les violations des règles de programmation et de conception énoncées dans les [instructions de conception .net](/dotnet/standard/design-guidelines/).

L'outil d'analyse représente les contrôles effectués lors d'une analyse comme messages d'avertissement. Les messages d'avertissement identifient les problèmes de programmation et de conception pertinents et, si possible, fournissent des informations relatives à leur résolution.

> [!NOTE]
> L’analyse héritée (analyse statique du code) n’est pas prise en charge pour les projets .NET Core et .NET Standard dans Visual Studio. Si vous exécutez l’analyse du code sur un projet .NET Core ou .NET Standard dans le cadre de MSBuild, vous verrez une erreur semblable à **Error : CA0055 : impossible d' \<your.dll> identifier la plateforme pour**. Pour analyser du code dans des projets .NET Core ou .NET Standard, utilisez à la place des [analyseurs de code](../code-quality/roslyn-analyzers-overview.md) .

## <a name="ide-integrated-development-environment-integration"></a>Intégration de l’IDE (environnement de développement intégré)

Vous pouvez exécuter l’analyse du code sur votre projet manuellement ou automatiquement.

Pour exécuter l’analyse du code chaque fois que vous générez un projet, sélectionnez l’option sur la page de propriétés **analyse du code** du projet. Pour plus d’informations, consultez [Comment : activer et désactiver l’analyse du code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Pour exécuter l’analyse du code manuellement sur un projet, dans la barre de menus, choisissez **analyser** exécuter l’analyse du code  >  **Run Code Analysis**  >  **exécuter l’analyse du code sur \<project>**.

## <a name="rule-sets"></a>Ensembles de règles

Les règles d’analyse du code pour le code managé sont regroupées dans des [ensembles de règles](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Vous pouvez utiliser l’un des ensembles de règles standard Microsoft, ou vous pouvez [créer un ensemble de règles personnalisé](../code-quality/how-to-create-a-custom-rule-set.md) pour satisfaire un besoin spécifique.

## <a name="suppress-warnings"></a>Supprimer les avertissements

Bien souvent, il est utile d'indiquer qu'un avertissement ne s'applique pas. Cela permet d’informer le développeur et les éventuels réviseurs de code, qu’un avertissement a fait l’objet d’une analyse, puis a été supprimé ou ignoré.

La suppression en source des avertissements est implémentée via des attributs personnalisés. Pour supprimer un avertissement, ajoutez l'attribut `SuppressMessage` au code source comme indiqué dans l'exemple suivant :

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Pour plus d’informations, consultez [supprimer des avertissements](../code-quality/in-source-suppression-overview.md).

::: moniker range="vs-2017"

> [!NOTE]
> Si vous migrez un projet vers Visual Studio 2017, vous serez peut-être confronté à un grand nombre d’avertissements d’analyse du code. Si vous n’êtes pas prêt à corriger les avertissements, vous pouvez les supprimer en choisissant **analyser**  >  **exécuter l’analyse du code et supprimer les problèmes actifs**.
>
> ![Exécuter l’analyse du code et supprimer les problèmes dans Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Si vous migrez un projet vers Visual Studio 2019, vous serez peut-être confronté à un grand nombre d’avertissements d’analyse du code. Si vous n’êtes pas prêt à corriger les avertissements, vous pouvez les supprimer en choisissant **analyser** la  >  **Build et supprimer les problèmes actifs**.

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Exécuter l’analyse du code dans le cadre de la stratégie d’archivage

En tant qu’organisation, vous pourriez demander à ce que tous les archivages respectent certaines stratégies. En particulier, vous souhaitez vous assurer que vous suivez ces règles :

- Il n’y a aucune erreur de build dans le code en cours d’archivage.

- L’analyse du code est exécutée dans le cadre de la build la plus récente.

Vous pouvez l'effectuer en spécifiant des stratégies d'archivage. Pour plus d’informations, consultez amélioration de la [qualité du code avec des stratégies d’archivage de projet](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Intégration Team Build

Vous pouvez utiliser les fonctionnalités intégrées du système de génération pour exécuter l'outil d'analyse dans le cadre du processus de génération. Pour plus d’informations, consultez [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs basés sur .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
- [Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Guide pratique pour activer et désactiver l’analyse du code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
