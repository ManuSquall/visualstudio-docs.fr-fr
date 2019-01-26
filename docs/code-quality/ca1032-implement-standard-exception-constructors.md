---
title: "CA1032 : Implémenter des constructeurs d'exception standard"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 947b22929c58ce962861c65946941513d7845152
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957780"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032 : Implémenter des constructeurs d'exception standard

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Étend un type <xref:System.Exception?displayProperty=fullName> mais ne déclare pas tous les constructeurs requis.

## <a name="rule-description"></a>Description de la règle

Types d’exception doivent implémenter les trois constructeurs suivants :

- NewException() public

- NewException(string) public

- publique NewException (string, Exception)

En outre, si vous exécutez l’analyse du code statique FxCop héritée en tant que contrairement à [analyseurs FxCop basée sur Roslyn](../code-quality/roslyn-analyzers-overview.md), l’absence d’un constructeur quatrième génère également une violation :

- protégé ou privée NewException (SerializationInfo, StreamingContext)

Ne pas fournir le jeu complet de constructeurs peut rendre difficile une gestion des exceptions correcte. Par exemple, le constructeur qui a la signature `NewException(string, Exception)` est utilisé pour créer des exceptions provoquées par d’autres exceptions. Sans ce constructeur, vous ne peut pas créer et lever une instance de votre exception personnalisée qui contient une exception interne (imbriquée), ce qui est le code managé doit faire dans une telle situation.

Les premiers constructeurs de trois exception sont publics par convention. Le quatrième constructeur est protégé dans les classes non scellés et privées dans les classes sealed. Pour plus d’informations, consultez [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, ajoutez les constructeurs manquants à l’exception et assurez-vous qu’ils ont l’accessibilité appropriée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle quand la violation est due à l’aide d’un niveau d’accès différent pour les constructeurs publics. En outre, il est OK supprimer l’avertissement pour le `NewException(SerializationInfo, StreamingContext)` constructeur si vous créez une bibliothèque de classes Portable (PCL).

## <a name="example"></a>Exemple

L’exemple suivant contient un type d’exception qui enfreint cette règle et un type d’exception qui est implémenté correctement.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Voir aussi

[CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)