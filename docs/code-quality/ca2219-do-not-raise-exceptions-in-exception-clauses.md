---
title: "CA2219 : Ne pas lever d'exceptions dans les clauses d'exception"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f8e949e21530654882cba99a7d9fedad8b5b59b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920271"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219 : Ne pas lever d'exceptions dans les clauses d'exception

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Catégorie|Microsoft.Usage|
|Modification avec rupture|Sans rupture, rupture|

## <a name="cause"></a>Cause
Une exception est levée à partir `finally`d’une clause, d’un filtre ou d’une clause Fault.

## <a name="rule-description"></a>Description de la règle
Quand une exception est levée dans une clause d’exception, cela augmente considérablement la difficulté du débogage.

Quand une exception est levée dans une `finally` clause or, la nouvelle exception masque l’exception active, le cas échéant. Cela rend l’erreur d’origine difficile à détecter et à déboguer.

Quand une exception est levée dans une clause de filtre, le Runtime intercepte l’exception en mode silencieux et fait en sorte que le filtre ait la valeur false. Il n’existe aucun moyen de déterminer la différence entre le filtre évalué à false et une exception levée à partir d’un filtre. Cela complique la détection et le débogage des erreurs dans la logique du filtre.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger cette violation de cette règle, ne levez pas explicitement d’exception à partir `finally`d’une clause, d’un filtre ou d’une clause Fault.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez pas un avertissement pour cette règle. Il n’existe aucun scénario dans lequel une exception levée dans une clause d’exception offre un avantage au code en cours d’exécution.

## <a name="related-rules"></a>Règles associées
[CA1065 Ne pas lever d’exceptions dans des emplacements inattendus](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Voir aussi
[Avertissements liés à la conception](../code-quality/design-warnings.md)