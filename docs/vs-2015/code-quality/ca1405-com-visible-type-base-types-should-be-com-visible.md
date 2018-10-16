---
title: 'CA1405 : Les types base type visibles par COM doivent être visibles par COM | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 43f18eb26cdbdf6ce97a17d2cc3f14dbecb62540
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200757"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405 : Les types de base type visibles par COM doivent être visibles par COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Présentation de l’Interface de classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) [interopération avec du Code non managé](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



