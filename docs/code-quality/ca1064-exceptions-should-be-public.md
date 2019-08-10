---
title: 'CA1064 : Les exceptions doivent être publiques'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b17ccfe66875588ac19c587ff6fcbd889d1e6a44
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922318"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064 : Les exceptions doivent être publiques

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une exception non publique dérive directement de <xref:System.Exception>, <xref:System.SystemException>ou <xref:System.ApplicationException>.

## <a name="rule-description"></a>Description de la règle
Une exception interne est visible uniquement à l’intérieur de sa propre portée interne. Lorsque l'exception se situe en dehors de la portée interne, seule l'exception de base peut être utilisée pour intercepter l'exception. Si l’exception interne est héritée de <xref:System.Exception>, <xref:System.SystemException>, ou <xref:System.ApplicationException>, le code externe n’aura pas d’informations suffisantes pour savoir que faire avec l’exception.

Toutefois, si le code a une exception publique qui est utilisée par la suite comme base pour une exception interne, il est raisonnable de supposer que le code plus éloigné pourra faire une opération intelligente avec l’exception de base. L’exception publique contient plus d’informations que celles fournies par <xref:System.Exception>, <xref:System.SystemException>ou <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Rendez l’exception publique ou dérivez l’exception interne d’une exception publique qui <xref:System.Exception>n' <xref:System.SystemException>est pas <xref:System.ApplicationException>, ou.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Supprimez un message de cette règle si vous êtes sûr, dans tous les cas, que l’exception privée sera interceptée dans sa propre étendue interne.

## <a name="example"></a>Exemple
Cette règle se déclenche sur la première méthode d’exemple, FirstCustomException, car la classe d’exception dérive directement de exception et est interne. La règle ne se déclenche pas sur la classe SecondCustomException, car bien que la classe dérive également directement d’exception, la classe est déclarée comme publique. La troisième classe ne déclenche pas non plus la règle, car elle ne dérive <xref:System.Exception?displayProperty=fullName>pas <xref:System.SystemException?displayProperty=fullName>directement de <xref:System.ApplicationException?displayProperty=fullName>, ou.

[!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
