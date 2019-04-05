---
title: 'CA2146 : Types doivent être au moins aussi critiques que leurs types de base et les interfaces | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d1a0120caf16fbed34fa87ab71fe50abc4467d51
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948599"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146 : Les types doivent être au moins aussi critiques que les types de base et les interfaces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type transparent est dérivé d’un type qui est marqué avec le <xref:System.Security.SecuritySafeCriticalAttribute> ou <xref:System.Security.SecurityCriticalAttribute>, ou un type qui est marqué avec le <xref:System.Security.SecuritySafeCriticalAttribute> attribut est dérivé d’un type qui est marqué avec le <xref:System.Security.SecurityCriticalAttribute> attribut.

## <a name="rule-description"></a>Description de la règle
 Cette règle se déclenche lorsqu’un type dérivé a un attribut de transparence de sécurité qui n’est pas aussi critique que son type de base ou l’interface implémentée. Seuls les types critiques peuvent dériver des types de base critiques ou implémenter des interfaces critiques, et seuls les types critiques ou critiques sécurisés peuvent dériver des types de base critiques sécurisés ou implémenter des interfaces critiques sécurisées. Les violations de cette règle dans la transparence de niveau 2 provoquent un <xref:System.TypeLoadException> pour le type dérivé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre cette violation, marquez le type dérivé ou d’implémentation avec un attribut de transparence est au moins aussi critique que le type de base ou interface.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]
