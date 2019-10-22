---
title: 'CA1405 : les types de base type visibles par COM doivent être visibles par COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 13a6f80bb0500286dd44e9c5ca9378e95d4b891d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661306"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405 : Les types de base type visibles par COM doivent être visibles par COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Category|Microsoft. Interoperability|
|Modification avec rupture|DependsOnFix|

## <a name="cause"></a>Cause
 Un type visible COM (Component Object Model) dérive d’un type qui n’est pas visible par COM.

## <a name="rule-description"></a>Description de la règle
 Quand un type visible par COM ajoute des membres dans une nouvelle version, il doit respecter des recommandations strictes pour éviter de rompre les clients COM qui sont liés à la version actuelle. Un type invisible à COM présume qu’il n’a pas besoin de suivre ces règles de contrôle de version COM lorsqu’il ajoute de nouveaux membres. Toutefois, si un type visible par COM dérive du type invisible COM et expose une interface de classe de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ClassInterfaceType> (valeur par défaut), tous les membres publics du type de base (à moins qu’ils soient spécifiquement marqués comme étant invisibles par COM, qui seraient redondants) sont exposés à COM. Si le type de base ajoute de nouveaux membres dans une version ultérieure, tous les clients COM qui sont liés à l’interface de classe du type dérivé risquent de s’arrêter. Les types visibles par COM doivent dériver uniquement des types visibles par COM pour réduire le risque d’interruption des clients COM.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez les types de base COM visibles ou le type dérivé COM invisible.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Présentation de l’interface de classe](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [interopérante avec du code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
