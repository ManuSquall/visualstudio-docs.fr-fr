---
title: "CA1903 : Utiliser uniquement l'API à partir du Framework cible"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d972198898dd1a4cafa5280c129db38bb3e4982
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921299"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903 : Utiliser uniquement l'API à partir du Framework cible

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Catégorie|Microsoft. Portability|
|Modification avec rupture|Rupture: lorsqu’elle est déclenchée par rapport à la signature d’un membre ou d’un type visible de l’extérieur.<br /><br /> Sans rupture: lorsqu’elle est déclenchée dans le corps d’une méthode.|

## <a name="cause"></a>Cause
Un membre ou un type utilise un membre ou un type qui a été introduit dans un Service Pack qui n’était pas inclus dans le Framework ciblé du projet.

## <a name="rule-description"></a>Description de la règle
De nouveaux membres et types ont été inclus dans .NET Framework 2,0 Service Pack 1 et 2, .NET Framework 3,0 Service Pack 1 et 2 et .NET Framework 3,5 Service Pack 1. Les projets qui ciblent les versions principales du .NET Framework peuvent non intentionnellement prendre des dépendances sur ces nouvelles API. Pour éviter cette dépendance, cette règle se déclenche sur les utilisations de tous les nouveaux membres et types qui n’ont pas été inclus par défaut avec le Framework cible du projet.

**Dépendances du Framework cible et du Service Pack**

|||
|-|-|
|Quand la version cible du .NET Framework|Se déclenche sur les utilisations des membres introduits dans|
|.NET Framework 2.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2|
|.NET Framework 3.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2, .NET Framework 3,0 SP1, .NET Framework 3,0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|N/A|

Pour modifier le Framework cible d’un projet, [consultez Procédure: Cibler une version de .NET](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour supprimer la dépendance sur le Service Pack, supprimez toutes les utilisations du nouveau membre ou du nouveau type. S’il s’agit d’une dépendance délibérée, supprimez l’avertissement ou désactivez cette règle.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez pas un avertissement de cette règle s’il ne s’agissait pas d’une dépendance délibérée sur le Service Pack spécifié. Dans ce cas, l’exécution de votre application risque d’échouer sur les systèmes sur lesquels cette Service Pack installée. Supprimez l’avertissement ou désactivez cette règle s’il s’agissait d’une dépendance délibérée.

## <a name="example"></a>Exemple
L’exemple suivant montre une classe qui utilise le type DateTimeOffset qui est uniquement disponible dans .NET 2,0 Service Pack 1. Cet exemple requiert que .NET Framework 2,0 ait été sélectionné dans la liste déroulante de la version cible du .NET Framework dans les propriétés du projet.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Exemple
L’exemple suivant résout la violation décrite précédemment en remplaçant les utilisations du type DateTimeOffset par le type DateTime.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>Voir aussi

- [Portability Warnings](../code-quality/portability-warnings.md)
- [Vue d’ensemble du ciblage des frameworks](../ide/visual-studio-multi-targeting-overview.md)