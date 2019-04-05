---
title: 'CA1903 : Utiliser uniquement l’API du framework cible | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e0382ab59745fccde53d09f88222b64d36a9bd6d
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59001822"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903 : Utiliser uniquement l'API à partir du Framework cible
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio, consultez [CA1903 : Utiliser uniquement l’API du framework cible](https://docs.microsoft.com/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework) sur docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Category|Microsoft.Portability|  
|Modification avec rupture|Avec rupture - lorsque déclenchée par rapport à la signature d’un type ou un membre extérieurement visible.<br /><br /> Sans rupture - lorsque déclenchée dans le corps d’une méthode.|  
  
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
  
 Pour modifier le framework cible d’un projet, consultez [ciblant une Version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour supprimer la dépendance sur le service pack, supprimez toutes les utilisations du nouveau membre ou type. S’il s’agit d’une dépendance délibérée, supprimez l’avertissement ou désactivez cette règle.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez pas un avertissement de cette règle si ce n’est pas une dépendance délibérée sur le service pack spécifié. Dans ce cas, votre application peut échouer à s’exécuter sur les systèmes sans ce service pack installé. Supprimer l’avertissement ou de désactiver cette règle s’il s’agissait d’une dépendance délibérée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une classe qui utilise le type DateTimeOffset est uniquement disponible dans .NET 2.0 Service Pack 1. Cet exemple nécessite que .NET Framework 2.0 a été sélectionné dans la liste déroulante Framework cible dans les propriétés du projet.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant corrige la violation précédemment décrite en remplaçant les utilisations du type DateTimeOffset par le type DateTime.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Avertissements de portabilité](../code-quality/portability-warnings.md)   
 [Cibler une version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
