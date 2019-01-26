---
title: 'CA1405 : Les types de base type visibles par COM doivent être visibles par COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: a94654475432706592c3cd2845488163529ca260
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943219"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405 : Les types de base type visibles par COM doivent être visibles par COM

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Category|Microsoft.Interoperability|
|Modification avec rupture|DependsOnFix|

## <a name="cause"></a>Cause
 Un type visible de composant COM (Object Model) dérive d’un type qui n’est pas visible par COM.

## <a name="rule-description"></a>Description de la règle
 Lorsqu’un type visible par COM ajoute des membres dans une nouvelle version, il doit se conformer strictement aux instructions pour éviter d’interrompre les clients COM liés à la version actuelle. Un type qui est invisible dans COM suppose qu’il n’a pas de suivre ces règles de versioning COM lorsqu’il ajoute de nouveaux membres. Toutefois, si un visibles par COM type dérive du type invisible par COM et expose une interface de classe de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ClassInterfaceType> (la valeur par défaut), tous les membres publics du type de base (sauf si elles sont spécifiquement marqués comme COM invisibles, ce qui serait redondant) sont exposées à COM. Si le type de base ajoute de nouveaux membres dans une version ultérieure, les clients COM qui se lient à l’interface de classe du type dérivé peuvent interrompre. Types visibles par COM doivent dériver uniquement de types visibles par COM afin de réduire le risque d’arrêt des clients COM.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rend les types de base visibles par COM ou le type dérivé COM invisible.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle.

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Interopération avec du code non managé](/dotnet/framework/interop/index)