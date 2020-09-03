---
title: 'CA1903 : utiliser uniquement l’API à partir du Framework ciblé | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 10649b4106a280089fd6b086167c7e92bff1300b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545247"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903 : Utiliser uniquement l'API à partir du Framework cible
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la documentation la plus récente sur Visual Studio, consultez [CA1903 : Use only API from Targeted Framework](/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework).

|Élément|Valeur|
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Category|Microsoft. Portability|
|Modification avec rupture|Rupture : lorsqu’elle est déclenchée par rapport à la signature d’un membre ou d’un type visible de l’extérieur.<br /><br /> Sans rupture : lorsqu’elle est déclenchée dans le corps d’une méthode.|

## <a name="cause"></a>Cause :
 Un membre ou un type utilise un membre ou un type qui a été introduit dans un Service Pack qui n’était pas inclus dans le Framework ciblé du projet.

## <a name="rule-description"></a>Description de la règle
 De nouveaux membres et types ont été inclus dans .NET Framework 2,0 Service Pack 1 et 2, .NET Framework 3,0 Service Pack 1 et 2 et .NET Framework 3,5 Service Pack 1. Les projets qui ciblent les versions principales du .NET Framework peuvent non intentionnellement prendre des dépendances sur ces nouvelles API. Pour éviter cette dépendance, cette règle se déclenche sur les utilisations de tous les nouveaux membres et types qui n’ont pas été inclus par défaut avec le Framework cible du projet.

 **Dépendances du Framework cible et du Service Pack**

|Élément|Valeur|
|-|-|
|Quand la version cible du .NET Framework|Se déclenche sur les utilisations des membres introduits dans|
|.NET Framework 2.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2|
|.NET Framework 3.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2, .NET Framework 3,0 SP1, .NET Framework 3,0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|N/A|

 Pour modifier le Framework cible d’un projet, consultez [ciblage d’une version spécifique de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour supprimer la dépendance sur le Service Pack, supprimez toutes les utilisations du nouveau membre ou du nouveau type. S’il s’agit d’une dépendance délibérée, supprimez l’avertissement ou désactivez cette règle.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle s’il ne s’agissait pas d’une dépendance délibérée sur le Service Pack spécifié. Dans ce cas, l’exécution de votre application risque d’échouer sur les systèmes sur lesquels cette Service Pack installée. Supprimez l’avertissement ou désactivez cette règle s’il s’agissait d’une dépendance délibérée.

## <a name="example"></a>Exemple
 L’exemple suivant montre une classe qui utilise le type DateTimeOffset qui est uniquement disponible dans .NET 2,0 Service Pack 1. Cet exemple requiert que .NET Framework 2,0 ait été sélectionné dans la liste déroulante de la version cible du .NET Framework dans les propriétés du projet.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]

## <a name="example"></a>Exemple
 L’exemple suivant résout la violation décrite précédemment en remplaçant les utilisations du type DateTimeOffset par le type DateTime.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]

## <a name="see-also"></a>Voir aussi
 [Avertissements de portabilité](../code-quality/portability-warnings.md) [ciblant une Version spécifique de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
