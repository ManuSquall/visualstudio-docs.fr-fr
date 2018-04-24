---
title: 'CA1405 : Les types de base type visibles par COM doivent être visibles par COM'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac8412e242f7d69ea657d5b7f74fa83ffbff5acc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405 : Les types de base type visibles par COM doivent être visibles par COM
|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Category|Microsoft.Interoperability|
|Modification avec rupture|DependsOnFix|

## <a name="cause"></a>Cause
 Un type visible du modèle COM (Component Object) dérive d’un type qui n’est pas visible par COM.

## <a name="rule-description"></a>Description de la règle
 Quand un type visible par COM ajoute des membres dans une nouvelle version, il doit se conformer aux recommandations strictes afin d’éviter l’interruption des clients COM qui se lient à la version actuelle. Un type qui est invisible dans COM suppose qu’il ne dispose pas de suivre ces règles de versioning COM lorsqu’il ajoute de nouveaux membres. Toutefois, si un visibles par COM type dérive du type invisible par COM et expose une interface de classe de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ClassInterfaceType> (la valeur par défaut), tous les membres publics du type de base (sauf si elles sont spécifiquement marquées comme COM invisibles, ce qui serait redondant) sont exposées à COM. Si le type de base ajoute de nouveaux membres dans une version ultérieure, les clients COM qui se lient à l’interface de classe du type dérivé peuvent interrompre. Types visibles par COM doivent dériver uniquement de types visibles par COM afin de réduire le risque d’interrompre les clients COM.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez les types visibles par COM de base ou le type dérivé COM invisible.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui enfreint la règle.

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Interopération avec du Code non managé](/dotnet/framework/interop/index)