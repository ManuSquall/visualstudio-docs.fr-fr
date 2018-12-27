---
title: 'CA1903 : Utiliser uniquement l’API du framework cible'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ace24746aafa70c73bc87c55c197913136f1a7b1
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53738870"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903 : Utiliser uniquement l’API du framework cible

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Category|Microsoft.Portability|
|Modification avec rupture|Avec rupture - lorsque déclenchée par rapport à la signature d’un type ou un membre extérieurement visible.<br /><br /> Sans rupture - lorsqu’il est déclenché dans le corps d’une méthode.|

## <a name="cause"></a>Cause
 Un membre ou un type utilise un membre ou un type qui a été introduit dans un service pack qui n’était pas inclus dans le framework ciblé du projet.

## <a name="rule-description"></a>Description de la règle
 Nouveaux membres et types ont été inclus dans .NET Framework 2.0 Service Pack 1 et 2, .NET Framework 3.0 Service Pack 1 et 2 et .NET Framework 3.5 Service Pack 1. Les projets qui ciblent les versions principales du .NET Framework peuvent involontairement prendre des dépendances sur ces nouvelles API. Pour éviter cette dépendance, cette règle se déclenche sur les utilisations de nouveaux membres et types qui n’étaient pas incluses par défaut avec le framework cible du projet.

 **Framework cible et les dépendances du Service Pack**

|||
|-|-|
|Lorsque le framework cible est|Se déclenche sur l’utilisation de membres introduits dans|
|.NET Framework 2.0|.NET framework 2.0 SP1, .NET Framework 2.0 SP2|
|.NET Framework 3.0|.NET framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|N/A|

 Pour modifier le framework cible d’un projet, consultez [ciblant une Version spécifique du .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour supprimer la dépendance sur le service pack, supprimez toutes les utilisations du nouveau membre ou type. S’il s’agit d’une dépendance délibérée, supprimez l’avertissement ou désactiver cette règle.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle si ce n’est pas une dépendance délibérée sur le service pack spécifié. Dans ce cas, votre application peut échouer à s’exécuter sur les systèmes sans ce service pack installé. Supprimer l’avertissement ou de désactiver cette règle s’il s’agissait d’une dépendance délibérée.

## <a name="example"></a>Exemple
 L’exemple suivant montre une classe qui utilise le type DateTimeOffset est uniquement disponible dans .NET 2.0 Service Pack 1. Cet exemple nécessite que .NET Framework 2.0 a été sélectionné dans la liste déroulante Framework cible dans les propriétés du projet.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Exemple
 L’exemple suivant corrige la violation précédemment décrite en remplaçant les utilisations du type DateTimeOffset par le type DateTime.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>Voir aussi

- [Portability Warnings](../code-quality/portability-warnings.md)
- [Cibler une version spécifique du .NET Framework](../ide/visual-studio-multi-targeting-overview.md)