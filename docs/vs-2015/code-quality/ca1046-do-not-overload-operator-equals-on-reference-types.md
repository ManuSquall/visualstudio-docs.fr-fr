---
title: 'CA1046 : Ne pas surcharger l’opérateur égal sur les types référence | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1f4f37f6d4c2662ca0b053e6737c57ba222b0b5e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588143"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046 : Ne pas surcharger l'opérateur égal à sur les types référence
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1046 : ne pas surcharger l’opérateur égal sur les types référence](https://docs.microsoft.com/visualstudio/code-quality/ca1046-do-not-overload-operator-equals-on-reference-types).

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type référence public ou imbriqué surcharge l’opérateur d’égalité.

## <a name="rule-description"></a>Description de la règle
 Pour les types référence, l’implémentation par défaut de l’opérateur d’égalité est presque toujours correcte. Par défaut, deux références sont égales uniquement si elles pointent sur le même objet.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez l’implémentation de l’opérateur d’égalité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle quand le type de référence se comporte comme un type valeur intégré. Si elle est significative pour effectuer une addition ou soustraction sur des instances du type, il est probablement correct d’implémenter l’opérateur d’égalité et de supprimer la violation.

## <a name="example"></a>Exemple
 L’exemple suivant montre le comportement par défaut lors de la comparaison de deux références.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante compare des références.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Cet exemple produit la sortie suivante.

 **un = nouveau (2,2) et b = nouveau (2,2) sont égaux ? Ne**
**c et a sont égaux ? Oui**
**b et a sont == ? Ne**
**c et a sont == ? Oui**
## <a name="related-rules"></a>Règles associées
 [CA1013 : Surchargez l’opérateur égal lors de la surcharge de l’opérateur d’addition et de soustraction](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Object.Equals%2A?displayProperty=fullName> [Opérateurs d’égalité](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



