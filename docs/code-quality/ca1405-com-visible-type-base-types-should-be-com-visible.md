---
title: 'CA1405 : Les types de base type visibles par COM doivent être visibles par COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e4e5c4ed258bcc88fedbb6d015fed576d326a0f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234955"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405 : Les types de base type visibles par COM doivent être visibles par COM

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Category|Microsoft. Interoperability|
|Modification avec rupture|DependsOnFix|

## <a name="cause"></a>Cause
Un type visible COM (Component Object Model) dérive d’un type qui n’est pas visible par COM.

## <a name="rule-description"></a>Description de la règle
Quand un type visible par COM ajoute des membres dans une nouvelle version, il doit respecter des recommandations strictes pour éviter de rompre les clients COM qui sont liés à la version actuelle. Un type invisible à COM présume qu’il n’a pas besoin de suivre ces règles de contrôle de version COM lorsqu’il ajoute de nouveaux membres. Toutefois, si un type visible par COM dérive du type invisible com et expose une interface de classe <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> de <xref:System.Runtime.InteropServices.ClassInterfaceType> ou (valeur par défaut), tous les membres publics du type de base (sauf s’ils sont spécifiquement marqués comme étant invisibles par com, qui seraient redondants) sont exposées à COM. Si le type de base ajoute de nouveaux membres dans une version ultérieure, tous les clients COM qui sont liés à l’interface de classe du type dérivé risquent de s’arrêter. Les types visibles par COM doivent dériver uniquement des types visibles par COM pour réduire le risque d’interruption des clients COM.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, rendez les types de base COM visibles ou le type dérivé COM invisible.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
L’exemple suivant montre un type qui viole la règle.

[!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Interopération avec du code non managé](/dotnet/framework/interop/index)