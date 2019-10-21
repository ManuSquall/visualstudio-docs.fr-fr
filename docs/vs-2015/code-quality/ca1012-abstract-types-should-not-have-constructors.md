---
title: 'CA1012 : les types abstraits ne doivent pas avoir de constructeurs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3f53e8b5eab78e79387c24643500888db27b764
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663231"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012 : Les types abstraits ne doivent pas avoir de constructeurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type public est abstrait et a un constructeur public.

## <a name="rule-description"></a>Description de la règle
 Les constructeurs des types abstraits peuvent être appelés uniquement par des types dérivés. Étant donné que les constructeurs publics créent des instances d'un type et que vous ne pouvez pas créer d'instance d'un type abstrait, un type abstrait doté d'un constructeur public est de conception incorrecte.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez le constructeur protégé ou ne déclarez pas le type comme abstract.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Le type abstrait a un constructeur public.

## <a name="example"></a>Exemple
 L’exemple suivant contient un type abstrait qui ne respecte pas cette règle.

 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/cs/FxCop.Design.AbstractTypeBad.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/vb/FxCop.Design.AbstractTypeBad.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant résout la violation précédente en modifiant l’accessibilité du constructeur de `public` à `protected`.

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/cs/FxCop.Design.AbstractTypeGood.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/vb/FxCop.Design.AbstractTypeGood.vb#1)]
