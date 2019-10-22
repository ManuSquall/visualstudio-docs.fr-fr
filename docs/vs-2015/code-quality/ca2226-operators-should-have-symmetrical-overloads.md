---
title: 'CA2226 : les opérateurs doivent avoir des surcharges symétriques | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9772577c2b1466cf3d1b5267129aa761db983021
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658908"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226 : Les opérateurs doivent contenir des surcharges symétriques
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type implémente l'opérateur d'égalité ou d'inégalité et n'implémente pas l'opérateur opposé.

## <a name="rule-description"></a>Description de la règle
 Il n’existe aucune circonstance dans laquelle l’égalité ou l’inégalité est applicable aux instances d’un type, et l’opérateur opposé n’est pas défini. Les types implémentent généralement l’opérateur d’inégalité en retournant la valeur de négation de l’opérateur d’égalité.

 Le C# compilateur émet une erreur pour les violations de cette règle.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez à la fois les opérateurs d’égalité et d’inégalité, ou supprimez celui qui est présent.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Votre type ne fonctionnera pas de manière cohérente avec l' [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="related-rules"></a>Règles associées
 [CA1046 : Ne pas surcharger l’opérateur égal sur les types de référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225 : Les surcharges d’opérateur ont d’autres méthodes nommées](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224 : Remplacez Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218 : Remplacez GetHashCode lors du remplacement de Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
