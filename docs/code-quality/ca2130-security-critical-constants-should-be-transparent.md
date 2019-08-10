---
title: 'CA2130 : Les constantes critiques de sécurité doivent être transparentes'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a33b650570981f5496813f575b1ae2413a960026
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920774"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130 : Les constantes critiques de sécurité doivent être transparentes

|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Catégorie|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un champ de constante ou un membre de l' <xref:System.Security.SecurityCriticalAttribute>énumération est marqué avec.

## <a name="rule-description"></a>Description de la règle
La mise en application de la transparence n’est pas effectuée pour les valeurs de constante car les compilateurs alignent les valeurs de constante afin qu’aucune recherche ne soit requise au moment de l’exécution. Les champs constants doivent être transparents de sécurité (security-transparent) afin que les relecteurs de code ne supposent pas que le code transparent ne peut pas accéder à la constante.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, supprimez l’attribut SecurityCritical du champ ou de la valeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
Dans les exemples suivants, la valeur `EnumWithCriticalValues.CriticalEnumValue` enum et la constante `CriticalConstant` déclenchent cet avertissement. Pour résoudre les problèmes, supprimez l'`SecurityCritical`attribut [] afin de rendre la sécurité transparente.

[!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]