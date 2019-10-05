---
title: "CA2136 : Les membres ne doivent pas avoir d'annotations de transparence conflictuelles"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f9455e83d7cb128a34696ae5e849fd0901f1891
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232219"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136 : Les membres ne doivent pas avoir d'annotations de transparence conflictuelles

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Cette règle se déclenche lorsqu’un membre de type est marqué <xref:System.Security> avec un attribut de sécurité qui a une transparence différente de l’attribut de sécurité d’un conteneur du membre.

## <a name="rule-description"></a>Description de la règle
Les attributs de transparence sont appliqués à partir d’éléments de code de plus grande portée à des éléments de plus petite portée. Les attributs de transparence d’éléments de code avec une plus grande portée sont prioritaires sur les attributs de transparence des éléments de code contenus dans le premier élément. Par exemple, une classe marquée avec l' <xref:System.Security.SecurityCriticalAttribute> attribut ne peut pas contenir une méthode marquée avec l' <xref:System.Security.SecuritySafeCriticalAttribute> attribut.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour résoudre ce problème, supprimez l’attribut de sécurité de l’élément de code qui a une portée inférieure, ou modifiez son attribut pour qu’il soit identique à l’élément de code conteneur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez pas les avertissements de cette règle.

## <a name="example"></a>Exemple
Dans l’exemple suivant, une méthode est marquée avec l' <xref:System.Security.SecuritySafeCriticalAttribute> attribut et il s’agit d’un membre d’une classe qui est marquée <xref:System.Security.SecurityCriticalAttribute> avec l’attribut. L’attribut Security SAFE doit être supprimé.

[!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]